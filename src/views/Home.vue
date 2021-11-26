<template>
  <div class="home">
<!--    Целевая функция-->
      <div class="flex flex-lg column">
        <div class="text-h6">Целевая функция: {{z[0]}}x<sub>1</sub> + {{z[1]}}x<sub>2</sub> + {{z[2]}}x<sub>3</sub> -> MAX</div>
        <div class="row " >
          <div id="z" class="fit row wrap justify-start items-start content-start" style="overflow: hidden;">
            <div class=" bg-grey-6" style="overflow: auto;">
              <q-card class="no-border-radius">
                <q-card-section>
                  <q-input square outlined mask="##" v-model="z[0]" label="z1" />
                </q-card-section>
              </q-card>
            </div><div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="##" v-model="z[1]" label="z2" />
              </q-card-section>
            </q-card>
          </div><div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="##" v-model="z[2]" label="z3" />
              </q-card-section>
            </q-card>
          </div>
          </div>
        </div>
    </div>
<!--    Ограничения-->
    <div class="flex flex-lg column">
      <div class="text-h6">Ограничения:</div>
      <div class="text-h6">  {{rests[0][0]}}x<sub>1</sub> + {{rests[0][1]}}x<sub>2</sub> + {{rests[0][2]}}x<sub>3</sub>  &le; {{rests[0][3]}} </div>
      <div class="text-h6"> {{rests[1][0]}}x<sub>1</sub> + {{rests[1][1]}}x<sub>2</sub> + {{rests[1][2]}}x<sub>3</sub>  &le; {{rests[1][3]}} </div>
      <div class="text-h6"> {{rests[2][0]}}x<sub>1</sub> + {{rests[2][1]}}x<sub>2</sub> + {{rests[2][2]}}x<sub>3</sub>  &le; {{rests[2][3]}} </div>
      <div class="row " >
        <div id="rest1" class="fit row wrap justify-start items-start content-start" style="overflow: hidden;">
          <div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="##" v-model="rests[0][0]"  />
              </q-card-section>
            </q-card>
          </div><div class=" bg-grey-6" style="overflow: auto;">
          <q-card class="no-border-radius">
            <q-card-section>
              <q-input square outlined mask="##" v-model="rests[0][1]"  />
            </q-card-section>
          </q-card>
        </div>
          <div class=" bg-grey-6" style="overflow: auto;">
          <q-card class="no-border-radius">
            <q-card-section>
              <q-input square outlined mask="##" v-model="rests[0][2]"  />
            </q-card-section>
          </q-card>
        </div>
          <div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="###" v-model="rests[0][3]"  />
              </q-card-section>
            </q-card>
          </div>
        </div>
      </div>
      <div class="row " >
        <div id="rest3" class="fit row wrap justify-start items-start content-start" style="overflow: hidden;">
          <div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="##" v-model="rests[1][0]"  />
              </q-card-section>
            </q-card>
          </div><div class=" bg-grey-6" style="overflow: auto;">
          <q-card class="no-border-radius">
            <q-card-section>
              <q-input square outlined mask="##" v-model="rests[1][1]"  />
            </q-card-section>
          </q-card>
        </div>
          <div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="##" v-model="rests[1][2]"  />
              </q-card-section>
            </q-card>
          </div>
          <div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="###" v-model="rests[1][3]"  />
              </q-card-section>
            </q-card>
          </div>
        </div>
      </div>
      <div class="row " >
        <div id="rest" class="fit row wrap justify-start items-start content-start" style="overflow: hidden;">
          <div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="##" v-model="rests[2][0]"  />
              </q-card-section>
            </q-card>
          </div><div class=" bg-grey-6" style="overflow: auto;">
          <q-card class="no-border-radius">
            <q-card-section>
              <q-input square outlined mask="##" v-model="rests[2][1]"  />
            </q-card-section>
          </q-card>
        </div>
          <div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="##" v-model="rests[2][2]"  />
              </q-card-section>
            </q-card>
          </div>
          <div class=" bg-grey-6" style="overflow: auto;">
            <q-card class="no-border-radius">
              <q-card-section>
                <q-input square outlined mask="###" v-model="rests[2][3]"  />
              </q-card-section>
            </q-card>
          </div>
        </div>
      </div>
    </div>
    <q-btn
        size="22px"
        class="q-px-xl q-py-xs"
        color="purple"
        label="Решить задачу"
        v-on:click=this.btn_clic()
    />
    <div class="text-h6">Решение:  {{solved}}</div>

<!--    <img alt="Vue logo" src="../assets/logo.png">-->
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {

  name: 'Home',
  components: {
    // HelloWorld
  },
  data: function () {
    return {
      z : [6, 1, 5],
      rests: [[7, 17, 17, 242],
             [16, 5, 1, 329],
             [18, 3, 3, 325]],
      solved:'',
    }
  },
  methods:{
  btn_clic (){
  alert('Ilya ne s\'el ezhika')
  },
  },
}
</script>
