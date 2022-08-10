<template>
    <div class="container has-text-centered">
        <div class="column is-6 is-offset-3">

            <div class="box">
                <h1 class="title">
                    Personal Code
                </h1>
                <div class="field is-grouped key">
                    <b-field>
                        <b-input v-model="perso1" placeholder="0000" minlength="4" maxlength="4" class="keynumber" size="is-large"></b-input>
                        <b-input v-model="perso2" placeholder="0000" minlength="4" maxlength="4" class="keynumber" size="is-large"></b-input>
                        <b-input v-model="perso3" placeholder="0000" minlength="4" maxlength="4" class="keynumber" size="is-large"></b-input>
                        <b-input v-model="perso4" placeholder="0000" minlength="4" maxlength="4" class="keynumber" size="is-large"></b-input>
                    </b-field>
                </div>
            </div>
            <div class="box">
                <h1 class="title">
                    Activation Code
                </h1>
                <div class="field is-grouped key">
                    <b-field>
                        <b-input v-model="activ1" placeholder="0000" minlength="4" maxlength="4" class="keynumber" size="is-large" disabled></b-input>
                        <b-input v-model="activ2" placeholder="0000" minlength="4" maxlength="4" class="keynumber" size="is-large" disabled></b-input>
                        <b-input v-model="activ3" placeholder="0000" minlength="4" maxlength="4" class="keynumber" size="is-large" disabled></b-input>
                        <b-input v-model="activ4" placeholder="0000" minlength="4" maxlength="4" class="keynumber" size="is-large" disabled></b-input>
                    </b-field>
                </div>
                <b-button type="is-primary" @click="generate">Generate</b-button>
                <p class="has-text-danger">{{ error }}</p>
            </div>
        </div>
    </div>
</template>


<script>
import axios from "axios";

export default {
  name: 'IndexPage',
  components: {
  },
  data() {
      return {
          perso1: "",
          perso2: "",
          perso3: "",
          perso4: "",
          activ1: "0000",
          activ2: "0000",
          activ3: "0000",
          activ4: "0000",
          error: ""
      }
  },
  methods: {
    generate() {
      const perso = ""+this.perso1+this.perso2+this.perso3+this.perso4;
      console.log(perso)
      if (perso.length !== 16) {
        this.error = "Personal Code is wrong"
      } else {
        this.error = ""
        axios.get("https://restless-bird-c5e0.nixgolf.workers.dev/?perso="+perso)
            .then(response => {
              if (response.data.error !== false) {
                this.error = response.data.error
              } else {
                let activkey = ""
                for (let i = 0; i < response.data.activation.length; i++) {
                  if (response.data.activation[i] > 9) {
                    activkey += "" + response.data.activation[i]
                  } else {
                    activkey += "0" + response.data.activation[i]
                  }
                }
                if (activkey.length !== 16) {
                  this.error = "Personal Code is wrong"
                } else {
                  this.activ1 = activkey.substring(0,4)
                  this.activ2 = activkey.substring(4,8)
                  this.activ3 = activkey.substring(8,12)
                  this.activ4 = activkey.substring(12,16)
                }
              }
            })
      }
    }
  }
}
</script>


<style>

.keynumber {
  width: 90px;
}

.key {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width:360px;
}

.box {
  background-color: rgba(20 20 20 / 50%);
}

</style>
