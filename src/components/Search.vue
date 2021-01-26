<template>

    <form @submit.prevent="getValue" style="justify-content: center; display: flex; align-items: baseline;">
      <ion-item>
            <ion-input  v-model="value" style="font-size:50px"></ion-input>
    </ion-item>
        <p style="font-size:100px">€</p>
    </form>
      
</template>

<script>
import {IonItem, IonInput } from '@ionic/vue';
// import axios from "axios";
export default {
  data(){
    return{
      value : "",
      weather : ""
    }
  },
  name: 'Form',
  components: {
      IonInput,
      IonItem,
      
  },
  methods: {
    displayError(message){
          const toast = document.createElement('ion-toast');
          toast.message = message;
          toast.duration = 2000;
          toast.color = "danger";
          document.body.appendChild(toast);
          return toast.present();
    },
    getValue(){
        console.log(this.value)
        if(!(parseFloat(this.value))){
            this.value = "";
            this.displayError("La valeur n'est pas valide (exemple : 11 ou 11,11). ");
            return;
        }
    //   let openWeatherMap = {
    //     key: "729172fe143c7159f66492956582b6a1",
    //   }

    //   axios
    //     .get("https://api.openweathermap.org/data/2.5/weather?q=" + this.nameCity +"&appid="+ openWeatherMap.key +"&lang=fr&units=metric")
    //     .then((response) => {
    //         this.weather = response.data;
    //         console.log(this.weather);
    //         this.$bus.emit("weather", this.weather);
    //     })
    //     .catch((error) => {
    //       console.log(error);
    //       const toast = document.createElement('ion-toast');
    //       toast.message = "Merci d'enter le nom d'une ville valide";
    //       toast.duration = 4000;
    //       toast.color = "danger";
    //       document.body.appendChild(toast);
    //       return toast.present();
    //     })
    },
  }
}
</script>
