<template >
   <form @submit.prevent="handleSubmit">
    <label>Email</label>
    <input type="email" name="email" required v-model="email" placeholder="Enter your email" />
    <label>Password</label>
    <input type="password" name="password" required v-model="password" placeholder="Enter password " />
    <label>Role:</label>
    <select name="role" required v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer"> Web Designer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="temSkill" @keyup.alt="addSkill"></input>
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>  
    </div>
    

    <div class="terms">
        <input type="checkbox" name="terms" required v-model="terms"/> 
        <label>agree to the terms and conditions</label> 
    </div>

    <div class="submit">
        
        <button> Create an account</button>
    </div>
    
   </form>
   <p>Email: {{ email }} </p>
   <p>Password: {{ password }} </p>
   <p>role: {{ role }} </p>
    <p>Terms: {{ terms }} </p>
   </template>
<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role:'developer',
            terms: false,
            temSkill: '',
            skills: [],
        }
    },
    methods: {
        addSkill(e){
           if(e.key === ',' && this.temSkill){
            if(!this.skills.includes(this.temSkill)){

                this.skills.push(this.temSkill)
            }
                
                this.temSkill = ''
            }
        },
        deleteSkill(skill){
            this.skills = this.skills.filter((item)=>{
                return item !== skill
            })
        },
        handleSubmit(){

        }
    },
}
</script>
<style >
form { 
max-width: 420px; 
margin: 30px auto; 
background: white; 
text-align: left; 
padding: 40px; 
border-radius: 10px; 
} 
label { 
color: #aaa; 
display: inline-block; 
margin: 25px 0 15px; 
font-size: 0.6em; 
text-transform: uppercase; 
letter-spacing: 1px; 
font-weight: bold; 
} 

input, select { 
display: block; 
padding: 10px 6px; 
width: 100%; 
box-sizing: border-box; 
border: none; 
border-bottom: 1px solid #ddd; 
color: #555; 
}

input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;

}

.pill{
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12x;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}

button{
    background: #0b6dff;
    border:0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;

}
.submit{
    text-align: center;
}

</style>