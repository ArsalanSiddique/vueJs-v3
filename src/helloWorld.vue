<template>
  <h1>Hello World VUE Js 3</h1>
  <!-- <p>I'm {{ name }}, from {{ country }}.</p>
  <p v-html="rawHTML"></p> -->

  <ul>
    <!-- <li v-for="(lang, index) in programmingLanguages" v-bind:key="lang.name">{{ index+1 }} - {{ lang.name }}</li> -->
    <li v-for="lang in programmingLanguages" v-bind:key="lang">{{ lang }}</li>
  </ul>
  <hr />
  <br />
  <p>Random Number: {{ number }}</p>

  <button @click="changeRandomNumber">Chage Random Number</button>
  <br />
  <br />
  <hr />
  <p>Two Way Binding: {{ num2 }}</p>
  <!-- <input :value="num2" @input="changeNum2($event)">  -->

  <input v-model="num2" />
  <button @click="change">Click Me</button>

  <br />
  <br />
  <hr />
  <input :value="txtValue" @keyup.enter="process($event)" />
  <p>{{ words.join(" | ") }}</p>

  <br />
  <hr />
  <br />
  <p>
    Your Score: {{ correct }} / {{ keywords.length }} ----------
    {{ countdown }} sec.
  </p>
  <p>
    <span
      :class="{
        correct: keyword.correct,
        wrong: keyword.wrong,
        pending: keyword.pending,
      }"
      :key="keyword.text"
      v-for="keyword in keywords"
    > 
      {{ keyword.text }}{{ "&nbsp;&nbsp;&nbsp;" }}
    </span>
  </p>
  <!-- <input v-if="countdown > 0 " :value="inputValue" @keyup.space="processInput($event)" />
  <input v-else disabled> -->
  <input :value="inputValue" @keyup.space="processInput($event)" />

</template>

<script>
export default {
  data() {
    // return {
    //   rawHTML: "<b> HTML </b>",
    //   name: "Arsalan Ahmed Siddique",
    //   country: "Pakistan",
    // };

    const defaultkeywords = [
      "Arsalan",
      "Ahmed",
      "Siddique",
      "Java",
      "Laravel",
      "Live-wire",
      "InertiaJs",
      "JetStream",
      "Github",
      "Jira",
      "DevOOPS",
      "Scrum",
      "Agile",
      "React",
      "angular",
      "codeigniter",
      "cakePhp",
      "prestashop",
      "VueJs",
      "expressJs",
      "nodeJs",
    ].map((keyword) => {
      return {
        text: keyword,
        correct: false,
        wrong: false,
        pending: true,
      };
    });

    return {
      // programmingLanguages: [
      //   { name: "JavaScript" },
      //   { name: "C" },
      //   { name: "C++" },
      //   { name: "Java" },
      //   { name: "Rust" },
      // ],

      // programmingLanguages: ["JavaScript", "C", "C++", "Java", "Rust"],

      programmingLanguages: {
        name: "JavaScript",
        creator: "I don't know.",
      },
      num2: 2,
      number: Math.random(),
      txtValue: "",
      index: 0,
      index1: 0,
      words: [],
      inputValue: "",
      correct: 0,
      countdown: 30,
      keywords: defaultkeywords,
    };

    // return {};
  },

  //   beforeCreate() {
  //     console.log("beforeCreate was called.");
  //   },
  //   created() {
  //     console.log("created was called.");
  //   },
  //   beforeMount() {
  //     console.log(this.name);
  //     console.log("beforeMount was called.");
  //   },
  //   mounted() {
  //     console.log("mounted was called.");
  //     // debugger;
  //   },
  //   beforeUnmount() {
  //     console.log("beforeUnmounted was called.");
  //   },
  //   unmounted() {
  //     console.log("unmounted was called.");
  //   },

  methods: {
    // showAlert() {
    //   alert("Alert Called by method.");
    // },

    changeRandomNumber() {
      this.number = Math.random();
      console.log("I was called");
    },
    change() {
      this.num2 = 100;
    },
    // changeNum2(e) {
    //   this.num2 = e.target.value;
    //   console.log(e.target.value);
    // }

    process(e) {
      const value = e.target.value;
      if (value === "") {
        return;
      } else {
        this.words[this.index1] = value;
        this.index1++;
        this.txtValue = "";
      }
    },

    processInput(e) {
      const input = e.target.value.trim();
      if (input === "") {
        return;
      }

      if (this.keywords[this.index].text === input) {
        // correct input
        this.keywords[this.index].correct = true;
        this.keywords[this.index].wrong = false;
        this.keywords[this.index].pending = false;
        this.correct++;
      } else {
        // wrong input
        this.keywords[this.index].correct = false;
        this.keywords[this.index].wrong = true;
        this.keywords[this.index].pending = false;
      }

      this.inputValue = "";
      this.index++;
    },

    countdownStart() {
      if (this.countdown > 0) {
        setTimeout(() => {
          this.countdown--;
          this.countdownStart();
        }, 1000);
      }
    },
  },
  created() {
    this.countdownStart();
  },
  mounted() {
    // this.showAlert();
  },
};
</script>

<style scoped>
.pending {
  font-weight: bold;
}
.correct {
  font-weight: bold;
  color: green;
}
.wrong {
  font-weight: bold;
  color: tomato;
}
</style>
