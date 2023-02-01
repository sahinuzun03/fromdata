<template>
    <form>
      <input type="text" v-model="text" />
      <!-- v-model ile data tarafına bağlamış oldum. -->
  
      <p>{{ text }}</p>
      <br>

      <!-- buraya v-model ile ayarladığım option seçtiğim anda bana değer olarak value içerisine yazılanları getirir eğer value değeri yoksa bize textleri value değeri olarak alıp getirir. -->
      <select v-model="framework">
        <option value="1">Vue</option>
        <option value="2">React</option>
        <option value="3">Angular</option>
      </select>
      <br>
      <p>{{ framework }}</p>
      <hr>
      <input type="checkbox" id="checkbox1" v-model="checked"/>
      <label for="checkbox1">Onay</label>
      <!-- for bu label'ın checkbox'a ait olduğunu belirttiğimiz şey. -->

      <p>Sonuç : {{ checked  ? 'Onaylıyorum' : 'Onaylamıyorum'}}</p>
      <br>
      <div>
        <input type="checkbox" id="Vue" value="Vue" v-model="frameworks"/>
        <label for="Vue">Vue</label>
      </div>
      <div>
        <input type="checkbox" id="React" value="React" v-model="frameworks"/>
        <label for="React">React</label>
      </div>
      <div>
        <input type="checkbox" id="Angular" value="Angular" v-model="frameworks"/>
        <label for="Angular">Angular</label>
      </div>
      <p>Seçilen Frameworkler : {{ frameworks }}</p>     

      <hr>
      <h3>Öğrenciler</h3>
      <input type="text" v-model="student" @keyup.alt="addStudent"/>
      <div v-for="student in students" :key="student">
        <span @click.prevent="deleteStudent(student)">
            {{ student }}
        </span>

        <!-- click.prevent ile beraber sayfanın yenilenmesini engellemiş oldum. -->
    </div>

    <br>
    <button @click="sendData">Gönder</button>
    </form>
    
  </template>
  
  <script>
  export default {
      data(){
          return{
              text:'Kutucuğa Bir İfade Giriniz',
              framework: 'Bir Değer Seçiniz',
              checked:false,
              frameworks:[],
              student:'',
              students:[]
          }
      },
      methods:{
        addStudent(e){
            if(e.key == ',' && this.student){
                if(!this.students.includes(this.student)){
                    this.students.push(this.student)
                }

                this.student = ''
            }
            
        },
        deleteStudent(student){
                this.students = this.students.filter(item => student !== item)

        },
        sendData(){
            console.log('Veriler gönderildi.')

        }
      }
  }
  </script>
  
  <style>
  </style>
  
  