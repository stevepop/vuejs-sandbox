<template>
  <div class="hello">
    <h2 class="mb-4">{{ msg }}</h2>

    <div class="container">
      <div class="row">
          <div class="col-sm">
            <div class="card">
              <div class="card-body">
                 <h4>DatePicker</h4>
                <el-date-picker
                  v-model="value1"
                  type="date"
                  format="dd/MM/yyyy"
                  value-format="yyyy-MM-dd"
                  placeholder="Pick a day">
                </el-date-picker>
                </div>
            </div>

            <div class="card">
              <div class="card-body">
                <h4>Transitions</h4>
                 <button v-on:click="show = !show" class="mt-2 mb-4">
                  Toggle transition
                 </button>
                  Duration: 
                  <input v-model="duration" type="range" min="100" max="3000">
                  {{duration}}ms
                  <fade-transition 
                    mode="out-in" 
                    :duration="durationNumber"
                  >
                     <div key="blue" v-if="show" class="box"></div>
                     <div key="red" v-else class="red-box"></div>
                  </fade-transition>
                  <fade-transition group :duration="300">
                    <div class="box" 
                        v-for="(item, index) in list" 
                        @click="remove(index)"
                        :key="item"
                    >
                    </div>
                  </fade-transition>

              </div>
            </div>
             
          </div>
          <div class="col-sm">
            <div class="card">
              <div class="card-body">
                   <h4>Slot Scopes</h4>
                  <links-list class="mt-5">
                    <div 
                      slot="link" 
                      slot-scope="{ link }"
                    >
                      <span v-show="link.bookmarked">
                          <svg xmlns="http://www.w3.org/2000/svg" width="8" height="8" viewBox="0 0 8 8">
                            <path d="M4 0l-1 3h-3l2.5 2-1 3 2.5-2 2.5 2-1-3 2.5-2h-3l-1-3z" />
                          </svg>
                      </span>
                      <a :href="link.href">
                        {{ link.title }}
                      </a>
                    </div>
                  </links-list>
              </div>
            </div>
          </div>
      </div>
  </div>
   

  </div>
</template>

<script>


import Modal from './Modal';
import Card from './Card'
import LinksList from './LinksList'
import FadeTransition from './FadeTransition'

export default {

  name: 'hello',

  components: { Modal, Card, LinksList, FadeTransition },

  computed: {
    durationNumber() {
      return parseInt(this.duration);
    }
  },

  data () {
    return {
      msg: 'My Vue.js Sandbox project',
      show: true,
      duration: 300,
      list: [1, 2, 3, 4, 5],
      value1: '',
    }
  },

  methods: {
    remove(index) {
      this.list.splice(index, 1);
    },
    addItem() {
      let randomIndex = Math.floor(Math.random() * this.list.length);
      this.list.splice(randomIndex, 0, Math.random());
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.box {
  width: 100px;
  height: 100px;
  margin-top: 20px;
  background-color: rgb(108, 141, 213);
  box-shadow: rgba(108, 141, 213, 0.5) 0px 6px 20px;
  border-radius: 10px;
}
.red-box {
  @extend .box;
  background-color: rgb(251, 17, 116);
  box-shadow: rgba(251, 17, 116, 0.5) 0px 6px 20px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
