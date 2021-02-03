<template>

  
    <form @submit.prevent style="justify-content: center; display: flex; align-items: baseline;">
      <ion-item style="margin-bottom: 50px ">
            <ion-input  v-model="value" style="font-size:25px" placeholder="Montant"></ion-input>
      </ion-item>
        <p style="font-size:50px">€</p>
    </form>

    <ion-item>
      <ion-label>Devise</ion-label>
      <ion-select v-model="selectedSymbol" value="brown" ok-text="Choisir" cancel-text="Annuler">
        <ion-select-option v-for="(value, key) in symbols" :value="key" :key="key" >{{ key }} : {{value }} </ion-select-option>
      </ion-select>
    </ion-item>

    <ion-button expand="block" @click.prevent="getValue"  style="margin: 20px 0" color="light">Convertir</ion-button>
      
</template>

<script>
import {
  IonItem,
  IonInput, 
  IonLabel, 
  IonSelect,
  IonSelectOption,
  IonButton
  } from '@ionic/vue';
import axios from "axios";


export default {
  data(){
    return{
      value : "",
      symbols : "",
      selectedSymbol : "",
      amount : "",
      result : ""
    }
  },
  name: 'Search',
  components: {
      IonInput,
      IonItem,
      IonLabel, 
      IonSelect,
      IonSelectOption,
      IonButton
  },
  mounted(){
      axios
        .get(`http://data.fixer.io/api/symbols?access_key=${process.env.VUE_APP_FIXER_KEY}`)
        .then((response) => {
            this.symbols = response.data.symbols;
        })
        .catch((error) => {
          console.log(error);
        })
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
        if (isNaN(this.value) || !this.value) {
          this.value = "";
          this.displayError("Nombre non valide. ");
          return;
        }

        if (!this.selectedSymbol){
          this.selectedSymbol = "";
          this.displayError("Merci de choisir une devise. ");
          return;
        }

        axios
        .get(`https://data.fixer.io/api/latest?access_key=${process.env.VUE_APP_FIXER_KEY}`)
        .then((response) => { 
            console.log(response.data.rates);
            let amountCurrency = response.data.rates[`${this.selectedSymbol}`]
            console.log(amountCurrency);
            let amount = amountCurrency * this.value;
            let result = amount.toFixed(2);
            this.$bus.emit("convert", `${result} ${this.selectedSymbol}`);
        })
        .catch((error) => {
          console.log(error);
            this.displayError("Une erreur est survenue. ");
        })

    },
  }
}
</script>
