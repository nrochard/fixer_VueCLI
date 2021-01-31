<template>
  <ion-app>
    <ion-header>
      <ion-toolbar>
        <ion-title>Convertisseur</ion-title>
      </ion-toolbar>
    </ion-header>

    <div class="ion-padding" id="container">
      
        <ion-row class="ion-align-items-center">
          <ion-col >
            <div>
              <search></search>
            </div>
          </ion-col>
        </ion-row>
        <ion-row class="">
          <ion-col>
            <result></result>
          </ion-col>
        </ion-row>
    </div>

    <ion-footer>
      <ion-toolbar>
        <ion-title>Powered by Fixer.io</ion-title>
      </ion-toolbar>
  </ion-footer>

  </ion-app>
</template>

<script>
import { IonApp, IonFooter, IonToolbar, IonHeader, IonTitle, IonRow, IonCol } from '@ionic/vue';
import Search from '../components/Search'
import Result from '../components/Result'

export default {
  name: 'Home',
  components: {
    // IonContent,
    IonApp,
    Search,
    IonFooter,
    IonToolbar,
    IonHeader,
    IonTitle,
    IonRow,
    IonCol,
    Result
  }
};
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>