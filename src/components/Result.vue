<template>
    <ion-card v-if="displayWeather == true">
        <ion-card-header>
            <ion-card-subtitle>{{ weatherCity.name }}</ion-card-subtitle>
            <ion-text> <h1 style="font-size: 70px"> {{img }} </h1> </ion-text>
            <ion-card-title> {{ weatherCity.main.temp }}° </ion-card-title>
        </ion-card-header>

        <ion-card-content>
        {{ weatherCity.weather[0].description }}
        </ion-card-content>
    </ion-card>
</template>

<script>
import { IonCard, IonCardContent, IonCardTitle, IonCardSubtitle, IonCardHeader, IonText} from '@ionic/vue';

export default {
    data(){
        return {
            weatherCity : {},
            displayWeather : false,
            img : ""
        }
    },
    name: 'Weather',
    components: {
        IonCard,
        IonCardContent,
        IonCardTitle,
        IonCardSubtitle,
        IonCardHeader,
        IonText
    },
}
</script>
