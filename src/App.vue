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
    <h4 v-if="num === 0">Num is Zero</h4>
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
    <p v-show="showUserName">
      This is username with display none prop on false
    </p>
    <p v-if="showUserName">This is username with only render in dom if true</p>

    <h1>List - V-For</h1>
    <h4 v-for="(userName, index) in names" :key="userName">
      {{ index }} {{ userName }}
    </h4>

    <div v-for="user in users" :key="user.name">
      <h2>{{ user.name }}</h2>
      <div v-for="tech in user.technology" :key="tech">{{ tech }}</div>
    </div>
    <template v-for="(info, key, index) in userInfo" :key="info">
      <p>{{ info }} {{ key }} {{ index }}</p>
    </template>

    <h1>List - Conditional Rendering</h1>
    <template v-for="userName in names" :key="userName">
      <h4 v-if="userName === 'Pandi'">{{ userName }}</h4>
    </template>

    <h1>Methods</h1>
    <h4>Add - {{ add(2, 10, 25) }}</h4>
    <h4>Multiply - {{ multiply(baseValue) }}</h4>

    <h1>Event Handlers</h1>
    <p>Name {{ name }}</p>
    <button @click="changeName($event), increment(5, $event)">
      Change Name
    </button>
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
      <input
        type="checkbox"
        id="agree"
        v-model="formData.agree"
        true-value="yes"
        false-value="no"
      />
      <button type="submit">Submit</button>
    </form>

    <h1>Form Control</h1>
    <pre>
      {{ JSON.stringify(modifiers, null, 2) }}
    </pre>
    <form @submit.prevent="formSubmit">
      <label for="fname">Name</label>
      <input type="text" id="fname" v-model.trim.lazy="modifiers.name" />
      <label for="age">Age</label>
      <input
        type="number"
        id="age"
        v-model.number="modifiers.age"
        @keyup.enter="formSubmit"
      />
    </form>

    <h1>Bonus Directives - V-Once, V-Pre</h1>
    <h2 v-once>{{ name }}</h2>
    <button @click="name = 'Changed Name'">Change Name</button>
    <h2 v-pre>{{ name }}</h2>

    <h1>Computed Properties</h1>
    <pre>
      computed: {
        fullName() {
          return `${this.userInfo.fname} ${this.userInfo.lname}`
        }
      }
    </pre>
    <h2>{{ fullName }}</h2>

    <h1>Computed Properties - Filter</h1>
    <pre>
      {{ JSON.stringify(items, null, 2) }}
    </pre>
    <h2>Expensive Item</h2>
    <ul>
      <li v-for="item in expensiveItem" :key="item.id">
        {{ item.name }} - {{ item.price }}
      </li>
    </ul>

    <h1>Computed Setter</h1>
    <h2>{{ computedSetter }}</h2>
    <button @click="changeComputedSetter">Change Name(Computer Setter)</button>

    <h1>Watchers</h1>
    <h2>Volume Range - 0 to 20</h2>
    <h2>Current Volume - {{ volume }}</h2>
    <button @click="volume += 2">Increase</button>
    <button @click="volume -= 2">Decrese</button>
    <p v-if="volumeAlert">{{ volumeAlert }}</p>

    <h1>Deep Watchers</h1>
    <input type="text" v-model.lazy="movie" />
    <p>Movie Details</p>
    <input type="text" v-model="movieInfo.name" />

    <h1>Component</h1>
    <GreetItem name="Bruce" heroName="Batman" />
    <GreetItem name="Clark" heroName="Superman" />
    <GreetItem :name="userInfo.fname" :hero-name="names[0]" />
    
    <h1>Component Props</h1>
    <ArticleItem name="Future of AI" :likes="50" :is-published="true" />

    <h1>Component NonProps - $attr</h1>
    <ArticleItem id="article-container" name="Attributes in vue" :likes="50" :is-published="true" />

    <h1>Provide & Inject</h1>
    <ParentItem />

    <h1>ComponentEvents</h1>
    <ComponentEvents />

    <h1>Custom Input</h1>
    <InputItem v-model="customInput"/>

    <h1>Slots</h1>
    <CardSlot></CardSlot>
    <CardSlot>Welcome to Vue</CardSlot>
    <CardSlot><h2>Welcome to Vue</h2></CardSlot>

    <h1>Named Slots</h1>
    <CardSlot>
      <template v-slot:header>Header</template>
      <template v-slot:default>Content</template>
      <template v-slot:footer>Footer</template>
    </CardSlot>

    <h1>Slots Props</h1>
    <NameListVue>
      <template v-slot:default="slotProps">
        {{ slotProps.lastName }} {{ slotProps.firstName }}
      </template>
    </NameListVue>

    <!-- New Integration -->
    <h1>Component Styles</h1>
    <ChildStyleVue></ChildStyleVue>
    <h4>This is h4 in App</h4>
    <CardSlot name="heading"><h4>This is slot h4</h4></CardSlot>

    <h1>Dynamic Component</h1>
    <DynamicComponentVue />
  </div>
</template>

<script>
import GreetItem from './components/Greet.vue';
import ArticleItem from './components/Article.vue';
import ParentItem from './components/Parent.vue';
import ComponentEvents from './components/ComponentEvents.vue';
import InputItem from './components/Input.vue';
import CardSlot from './components/Slot.vue';
import NameListVue from './components/NameList.vue';
import ChildStyleVue from './components/ChildStyle.vue';
import DynamicComponentVue from './components/DynamicComponent.vue';

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
      names: ["Brain", "Bruce", "Hary"],
      users: [
        {
          name: "Pandi",
          technology: ["html", "nodejs", "react", "vue"],
        },
        {
          name: "Selvam",
          technology: ["html", "nodejs", "react"],
        },
        {
          name: "Mohammed",
          technology: ["html", "nodejs", "react"],
        },
      ],
      userInfo: {
        fname: "Pandiarajan",
        lname: "Rajagopal",
        id: "29",
      },
      baseValue: 2,
      baseMultiply: 5,
      count: 0,
      formData: {
        name: "",
        agree: "",
      },
      modifiers: {
        name: "",
        age: null,
      },
      items: [
        {
          id: 1,
          name: "TV",
          price: 100,
        },
        {
          id: 2,
          name: "AC",
          price: 200,
        },
        {
          id: 3,
          name: "Fridge",
          price: 300,
        },
      ],
      volume: 0,
      volumeAlert: "",
      movie: "",
      movieInfo: {
        name: 'Batman',
        year: 2005
      },
      customInput: ''
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
      console.log("Event", event);
      this.name = "Vue Giant";
    },
    formSubmit(event) {
      event.preventDefault();
      console.log("Form Values", this.formData.name);
    },
    changeComputedSetter() {
      this.computedSetter = "Welcome Nature";
    },
  },
  computed: {
    fullName() {
      return `${this.userInfo.fname} ${this.userInfo.lname}`;
    },
    expensiveItem() {
      return this.items.filter((i) => i.price > 100);
    },
    computedSetter: {
      get() {
        return `${this.userInfo.fname} ${this.userInfo.lname}`;
      },
      set(value) {
        const [fname, lname] = value.split(" ");
        this.userInfo.fname = fname;
        this.userInfo.lname = lname;
      },
    },
  },
  watch: {
    volume(newValue) {
      if (newValue > 16) {
        this.volumeAlert = "Please reduce the volume it will hurt your ear";
      } else {
        this.volumeAlert = "";
      }
    },
    movie: {
      handler(newValue) {
        console.log("new Movie", newValue);
      },
      immediate: true,
    },
    movieInfo: {
      handler(newValue) {
        console.log('Movie Info', newValue)
      },
      deep: true
    },
  },
  components: {
    GreetItem,
    ArticleItem,
    ParentItem,
    ComponentEvents,
    InputItem,
    CardSlot,
    NameListVue,
    ChildStyleVue,
    DynamicComponentVue
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
h4 {
  color: goldenrod;
}
</style>
