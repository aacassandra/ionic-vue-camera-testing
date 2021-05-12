<template>
  <div id="container">
    <strong>{{ name }}</strong>
    <p>Explore <a target="_blank" rel="noopener noreferrer" href="https://ionicframework.com/docs/components">UI Components</a></p>
    <ion-button @click="methods.getImage()">Get Image</ion-button>
  </div>
</template>

<script>
import {IonButton} from '@ionic/vue'
import {Plugins, CameraSource, CameraResultType} from '@capacitor/core'

const {Camera} = Plugins
export default {
  name: 'ExploreContainer',
  props: {
    name: String
  },
  components:{
    IonButton
  },
  setup() {
    const methods = {
      getImage: () => {
        Camera.getPhoto({
          quality: 100,
          source: CameraSource.Camera,
          resultType: CameraResultType.Base64
        }).then((res) => {
          console.log(res)
        })
      }
    }

    return {
      methods
    }
  }
}
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