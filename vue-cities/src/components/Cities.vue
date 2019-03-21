<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    {{name}}

    {{btnState ? 'The button is disabled':'The button is enabled'}}

    <button v-on:click="changeName" v-bind:disabled="btnState">
      Change Name on Click of this button
    </button>

    <div class="holder">
      <ul>
        <li v-for="(data1, index) in cities" :key="index">
          {{index}} . {{data1.city}}
        </li>
      </ul>

      <p v-if="cities.length >= 2"> You have more than 2 cities</p>
      <p v-else> You have less than 2 cities</p>



    </div>

    
      <div v-bind:class="{ alert1: showPropertyAlert, 'second': showSecondClass}">
        Text with class binding for style
      </div>
      <br />
      <div v-bind:style="{backgroundColor:bgColor, width: bgWidth  }">
        text with style binding for styling
      </div>

      <br />


      <form @submit.prevent="addCity">
      <input type="text" placeholder="Enter another city" v-model="mcity" v-validate="'min:3'" name="mcity">
      <p class="alert" v-if="errors.has('mcity')">
        {{errors.first('mcity')}}
        </p>

      <input type="checkbox" id="chkbox" v-model="checked" />
      </form>
      <h3>{{mcity}}</h3>
  </div>
</template>

<!-- v-bind:class="{ alert:showPropertyAlert} means that use the class alert from the styles
if the boolean showPropertyAlert is true -->

<script>
export default {
  name: 'Cities',
  props: {
    msg: String
  },
  data() {
    return {
      name: 'Cities Component Name',
      btnState: true,
      mcity: '',
      checked: false,
      cities: [
        {"city": "Mumbai"},
        {"city": "New York"},
        {"city": "Copenhagen"},
        
      ],
      showPropertyAlert: true,
      showSecondClass: true,
      bgColor: 'tomato',
      bgWidth: '100%'
      
    }
  },
  methods: {
    addCity() {
      this.cities.push({city: this.mcity});
      console.log(this.cities);
      this.mcity='';
      console.log(this.checked);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<!-- This means only inside this specific component -->
<!--in case, we use src, we can put styles in different files and then remove the styles
from here below. just keep the style tag  -->

<!-- <style src="./Cities.css" scoped> -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
.holder {
  background-color: thistle;
}
.alert1 {
 background-color: yellow;
 width: 100%;
 height: 30%;
}
.second {
  border: 5px solid #42b983 ;
}
input {
  width: calc(100% - 40px);
  border: 1px;
  padding: 20px;
  font-size: 1.3em;
  background-color: #eeeeee;
  color: #687f7f;
}
</style>
