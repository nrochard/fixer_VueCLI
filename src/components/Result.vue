<template>
    <div style="font-size: 40px">
       <ion-card v-if="result">
            <ion-card-header>
                <ion-card-subtitle>Résultat : </ion-card-subtitle>
                <ion-card-title> {{result}} </ion-card-title>
            </ion-card-header>
        </ion-card>
    </div>
</template>

<script>
import { } from '@ionic/vue';
import {
  IonCard,
  IonCardHeader, 
  IonCardSubtitle, 
  IonCardTitle
  } from '@ionic/vue';


export default {
    data(){
        return {
            result : ""
        }
    },
    name: 'Result',
    components: {
        IonCardHeader,
        IonCardSubtitle,
        IonCard,
        IonCardTitle
    },
    mounted(){
        this.$bus.on('convert', (result) => {
        this.result = result;
        console.log(result)
        })

        // axios
        // .get(`http://data.fixer.io/api/latest?access_key=${process.env.VUE_APP_FIXER_KEY}`)
        // .then((response) => { 
        //     console.log(response.data);
        // })
        // .catch((error) => {
        //   console.log(error);
        // //   const toast = document.createElement('ion-toast');
        // //   toast.message = "Merci d'enter le nom d'une ville valide";
        // //   toast.duration = 4000;
        // //   toast.color = "danger";
        // //   document.body.appendChild(toast);
        // //   return toast.present();
        // })
    },
}
</script>
