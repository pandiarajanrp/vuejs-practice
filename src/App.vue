<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>Variable Binding</h1>
    <h4>{{ name }}</h4>
    <h1>V-Bind</h1>
    <div class="underline" v-bind:class="status">This is text</div>
    <div v-bind:id="containerId">This is content container</div>
    <p v-bind:class="isPromoted && 'promoted'">This is promoted content</p>
    <p v-bind:class="isSoldOut ? 'soldout' : 'new'">Soldout Movie</p>
    <p v-bind:class="[isPromoted && 'promoted', isSoldOut ? 'soldout' : 'new']">
      Array Conditional Text
    </p>
    <p
      v-bind:class="{
        promoted: isPromoted,
        soldout: isSoldOut,
        new: isNew,
      }"
    >
      Object conditional class binding
    </p>
    <h1>V-Bind Shorthand</h1>
    <p :class="isShort ? 'short' : 'non-short'">V bind Shorthand</p>

    <h1>Conditional Rendering</h1>
    <h4 v-if="num===0">Num is Zero</h4>
    <h4 v-else-if="num > 0">Positive</h4>
    <h4 v-else-if="num < 0">Negative</h4>
    <h4 v-else>Not a Number</h4>

    <h1>Conditional Rendering With Multiple Element</h1>
    <template v-if="showConditions">
      <p>Terms and conditions</p>
      <p>Privacy Policy</p>
      <p>Agree to Policy</p>
    </template>

    <h1>CR - V-Show</h1>
    <p v-show="showUserName">This is username with display none prop on false</p>
    <p v-if="showUserName">This is username with only render in dom if true</p>

    <h1>List - V-For</h1>
    <h4 v-for="(userName, index) in names" :key="userName">{{ index }} {{ userName }}</h4>

    <div v-for="user in users" :key="user.name">
      <h2>{{ user.name }}</h2>
      <div v-for="tech in user.technology" :key="tech">{{ tech }}</div>
    </div>
    <template v-for="(info, key, index) in userInfo" :key="info">
      <p>{{ info }} {{ key }} {{ index }}</p>
    </template>

    <h1>List - Conditional Rendering</h1>
    <template v-for="(userName) in names" :key="userName">
      <h4 v-if="userName === 'Pandi'"> {{ userName }}</h4>
    </template>

    <h1>Methods</h1>
    <h4>Add - {{ add(2,10,25) }}</h4>
    <h4>Multiply - {{ multiply(baseValue) }}</h4>

    <h1>Event Handlers</h1>
    <p>Name {{ name }}</p>
    <button @click="changeName($event), increment(5, $event)">Change Name</button>
    <p>{{ count }}</p>
    <button v-on:click="count++">Increment By 1</button>
    <button v-on:click="increment(5)">Increment By 5</button>

    <h1>Form Control</h1>
    <h4>Preview</h4>
    <pre>
      {{ JSON.stringify(formData, null, 2) }}
    </pre>
    <form @submit="formSubmit">
      <label for="name">Name</label>
      <input type="text" id="name" v-model="formData.name" />
      <label for="agree">Agree?</label>
      <input type="checkbox" id="agree" v-model="formData.agree" true-value="yes" false-value="no">
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "Welcome to Vue JS",
      status: "danger",
      containerId: "content-wrapper",
      isPromoted: true,
      isSoldOut: false,
      isNew: true,
      isShort: true,
      num: 5,
      showConditions: true,
      showUserName: true,
      names: ['Pandi', 'Selvam', 'Mohammed'],
      users: [
        {
          name: "Pandi",
          technology: ["html", "nodejs", "react", "vue"]
        },
        {
          name: "Selvam",
          technology: ["html", "nodejs", "react"]
        },
        {
          name: "Mohammed",
          technology: ["html", "nodejs", "react"]
        }
      ],
      userInfo: {
        fname: "Pandiarajan",
        lname: "Rajagopal",
        id: '29'
      },
      baseValue: 2,
      baseMultiply: 5,
      count: 0,
      formData: {
        name: '',
        agree: ''
      }
    };
  },
  methods: {
    add(a, b, c) {
      return a + b + c;
    },
    multiply(num) {
      return num * this.baseMultiply;
    },
    increment(num) {
      this.count += num;
    },
    /**
     * do not use arrow function in methods as its context changes to only methods
     
    multiply: (num) => {
      return this.baseMultiply * num
    }
    this will break the js 
    */
    changeName(event) {
      console.log('Event', event)
      this.name = 'Vue Giant'
    },
    formSubmit(event) {
      event.preventDefault()
      console.log('Form Values', this.formData.name)
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.promoted {
  font-style: italic;
}
.soldout {
  color: red;
}
.new {
  color: green;
  font-weight: bold;
}
.short {
  color: magenta;
}
h1 {
  border: 1px solid #eee;
}
</style>
