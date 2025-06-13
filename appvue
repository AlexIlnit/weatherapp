<script>
import User from './components/User.vue'
import axios from 'axios'

export default {
    components: { User },
    data() {
      return {
          city: '',
          // users: [],
          error: '',
          // userName: '',
          // userPass: '',
          // userEmail: ''
          info: null
      }
    },
    computed: {
      cityName() {
        return "* " + this.city + " *"
      },
      showTemp() {
        return "Температура: " + this.info.temp
      },
      showFeelsLike() {
        return "Ощущается как: " + this.info.feels_like
      },
      showMinTemp() {
        return "Минимальная температура " + this.info.temp_min
      },
      showMaxTemp() {
        return "Максимальная температура " + this.info.temp_max
      }

    },
    methods: {
      getWeather() {
        if(this.city.trim().length < 2){
            this.error = "Нужно название больше одного символа ;)"
            return false
        }
          this.error = '',

          axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=fef2a8c9a0a7f563a620a2154f040cef`)
            .then(res => (this.info = res.data.main))
      }
      // sendData() {
      //   if(this.userName == '') {
      //     this.error = 'Имя не введено';
      //     return;
      //   } else if(this.userEmail == '') {
      //     this.error = 'Email не введен';
      //     return;
      //   }else if(this.userPass == '') {
      //     this.error = 'Pass не введен';
      //     return;
      //   }

      //   this.error = '';
      //   this.users.push({
      //     name: this.userName,
      //     pass: this.userPass,
      //     email: this.userEmail
      //   })
      // },
      // deleteUser(index) {
      //   this.users.splice(index, 1);
      // }
    }
}
</script>
<template>
  <div class="wrapper">
    <h1>Погодное приложение </h1>
    <p>Узнать погоду в {{ city == "" ? "вашем городе" : cityName }}</p>
    <!-- <input type="text" v-on:input="this.city = $event.target.value" placeholder="Введите город">  -->
    <!-- <input type="text" @input="this.city = $event.target.value" placeholder="Введите город">  -->
    <input type="text" v-model="city" placeholder="Введите город"> 
    <!-- <button v-show="city != '' ">Получить погоду</button> -->
     <button v-if="city != '' " @click="getWeather()">Получить погоду</button>
     <button disabled v-else>Введите название города</button>
     <p class="error">{{ error }}</p>
    
    <div v-if="info != null">
      <p>{{ showTemp }}</p>
      <p>{{ showFeelsLike }}</p>
      <p>{{ showMinTemp }}</p>
      <p>{{ showMaxTemp }}</p>
    </div>
  </div>

</template>

<style scoped>
.error {
  color: #d03939;
}
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: #1f0f24;
  padding: 20px;
  text-align: center;
  color: white;
}
.wrapper h1 {
  margin-top: 50px;
}
.wrapper p {
  margin-top: 20px;
}
.wrapper input {
  margin-top: 30px;
  background: transparent;
  border: 0;
  border-bottom: 2px solid #110813;
  color: #fcfcfc;
  font-size: 14px;
  padding: 5px 8px;
  outline: none;
}
.wrapper input:focus {
  border-bottom-color: #6e2d7d;
}
.wrapper button:disabled {
  background: #71580e;
  cursor: not-allowed;
}
.wrapper button {
  background: #e3bc4b;
  color: #fff;
  border-radius: 10px;
  border: 2px solid #b99935;
  padding: 10px 15px;
  margin-left: 20px;
  cursor: pointer;
  transition: transform 500ms ease;
}
.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}
</style>
