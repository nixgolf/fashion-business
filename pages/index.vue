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
                <b-button type="is-primary">Generate</b-button>
            </div>
        </div>
    </div>
</template>


<script>

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
