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
        })
    },
}
</script>
