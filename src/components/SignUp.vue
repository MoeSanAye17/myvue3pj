<template>
    <form @submit.prevent="submit">
        <label for="">Email</label>
        <!--v-model is used for two way data binding-->
        <input type="email" required v-model="email">

        <label for="">Password</label>
        <input type="password" v-model="password">
        <p class="error">{{errorMsg}}</p>

        <label for="">Roles:</label>
        <select v-model="role">
            <option value="developer">Web Developer</option>
            <option value="designer">Web Designer</option>
        </select>

        <div>
            <label for="">Skills</label>
            <input type="text" @keyup.alt="addSkill" v-model="skill">
        </div>

        <div v-for="skill in skills" :key="skill" @click="deleteSkill(skill)">
            <p>{{skill}}<span class="cross">&#x2716;</span></p>
        </div>

        <div>
            <!--write single checkbox and save true(click) default is false-->
            <input type="checkbox" v-model="accept">
            <label for="">Accept Terms and condition</label>
        </div>

        <div class="align">
            <button class="create">Create Account</button>
        </div>
        <!--multiple checkbox need value and save array-->
        <!-- <label for="">check names</label>
        <div>
           <input type="checkbox" value="moesanaye" v-model="names">
           <label for="">moesanaye</label>
        </div>
        <div>
            <input type="checkbox" value="mgmg" v-model="names">
            <label for="">mgmg</label>
        </div>
        <div>
            <input type="checkbox" value="kyawkyaw" v-model="names">
            <label for="">kyawkyaw</label>
        </div>-->
    </form>
        <p>email - {{email}}</p>
        <p>password - {{password}}</p>
        <p>role - {{role}}</p>
        <p>accept - {{accept}}</p>
        <p>names - {{names}}</p>
</template>

<script>
export default {
    data(){
        return{
            email:"",
            password:"",
            role:"",
            accept:false,
            names:[],
            skills:[],
            skill:"",
            errorMsg:""
        }
    },
    methods:{
        addSkill(event){
            if(event.key === ","){
                this.skills.push(this.skill);
                this.skill=""
            }
        },
        deleteSkill(skill){
            this.skills=this.skills.filter(loopSkill =>{
                return loopSkill != skill;
            })
        },
        submit(){
            if(this.password.length<8){
                this.errorMsg="Password must be at least 8 characters"
            }
        }
    }
}
</script>

<style>
    form{
        max-width: 300px;
        margin: 30px auto;
        background: white;
        text-align: left;
        padding: 20px;
        border-radius: 10px;
    }
    label{
        color: rgb(98, 191, 245);
        display: inline-block;
        margin: 25px 0 15px;
        font-size: 0.6em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
    }
    input,select{
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
    }
    input[type="checkbox"]{
        display: inline-block;
        width: 16px;
        margin: 0 10px 0 0;
        position: relative;
        top: 2px;
    }
    .cross{
        cursor: pointer;
        color: red;
    }
    .create{
        background-color: royalblue;
        padding: 8px;
        color: white;
        border-radius: 10px;
    }
    .align{
        text-align: center;
    }
    .error{
        color: crimson;
        font-size: 10px;
    }
</style>