<template>
        <form @submit.prevent="submitItem">
            <div class="mail">
                <span>Email</span>
                <input type="email" required>
            </div>
            
            <div class="pee">
                <label>Password</label>
                <input type="password" required>
                <span v-if="passwordError" class="error">{{ passwordError }}</span>
            </div>

            <div class="web">
                <span>Role: </span>
                <select>
                    <option value="web developer"></option>
                    <option value="web designer"></option>
                </select>
            </div>

            <div class="tee">
                <span>Skills</span>
                <input type="text" required @keyup.alt="addSkill" v-model="mySkills">
                <h4 v-for="skill in skills" :key="skill" id="pill" >
                    <span @click="deleteSkill(skill)" class="spin">{{ skill }}</span>
                </h4>
            </div>

            <div class="terms">
                <input type="checkbox" required>
                <label>Accept terms</label>
            </div>

            <button class="btn">Submit</button>



        </form>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            terms: false,
            role: 'web dev',
            mySkills: ' ',
            skills: [ ],
            passwordError: ' '
        }
    },
    methods: {
        addSkill(e) {
            if ( e.key === ',' && this.mySkills){
                this.skills.push(this.mySkills)
                this.mySkills = " "
            }
        },
        deleteSkill(skill) {
            this.skills = this.skills.filter((item) => {
                return skill !== item
            })
        },
        submitItem() {
            this.passwordError = this.password.length > 5 ? 
            ' ' : 'password must be up up to 6 chars or more'
        }
    }

}

</script>

<style scoped>
form{
    max-width: 600px;
    border: 1px solid white;
    padding: 20px auto;
    background: white;
}
.mail {
    margin: 20px 20px;
    padding: 5px;
}
.mail span{
    margin-right: 500px;
}
.mail input{
    width: 420px;
    height: 23px;
    border-radius: 6px;
    color: grayscale;
    
}
.pee label{
    margin-right: 360px;
}
.pee input{
    width: 420px;
    height: 23px;
    border-radius: 6px;
}
.web{
    margin: 25px;
}
.web span{
    margin-right: 390px;
}
.web select{
    width: 420px;
    height: 33px;
    border-radius: 6px;   
}
.web select option {
    font-size: 20px;
    background-color: white;
    color: black;
}
.terms{
    margin-top: 24px;
    margin-right: 310px;
}
.tee {
    margin-right: 380px;
    padding: 20px 0;
}
.tee input{
    width: 420px;
    height: 23px;
    margin-left: 29px;
    border-radius: 6px;
}
.spin{
    background: grey;
    padding: 10px;
    border-radius: 20px;
    color: white;
    cursor: pointer;
}
#pill{
    display: inline-block;
    margin: 20px 10px 0 0;
}
.btn {
    background: skyblue;
    padding: 6px;
    border-radius: 4px;
    margin-top: 15px;
}
.error{
    color: brown;
    font-weight: bold;
}

</style>