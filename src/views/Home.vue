<template>
  <ion-app>
    <ion-header>
      <ion-toolbar>
        <ion-title>Header</ion-title>
      </ion-toolbar>
    </ion-header>

    <div class="ion-padding" id="container">
      
        <ion-row class="ion-align-items-center">
          <ion-col >
            <div>
              <Form></Form>
            </div>
          </ion-col>
        </ion-row>
        <ion-row class="">
          <ion-col>
            <div>
              2 of 4
            </div>
          </ion-col>
        </ion-row>
    </div>

    <ion-footer>
      <ion-toolbar>
        <ion-title>Footer</ion-title>
      </ion-toolbar>
  </ion-footer>

  </ion-app>
</template>

<script>
import { IonApp, IonFooter, IonToolbar, IonHeader, IonTitle, IonRow, IonCol } from '@ionic/vue';
import Form from '../components/Search'
// import Weather from '../components/Result'

export default {
  name: 'Home',
  components: {
    // IonContent,
    IonApp,
    Form,
    IonFooter,
    IonToolbar,
    IonHeader,
    IonTitle,
    IonRow,
    IonCol
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