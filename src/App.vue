<template>
  <div class="wrapper">
    <main class="calculator">
      <h1>Calculator</h1>
      <form class="operation">
        <!-- Binds variables to inputs -->
        <input
          v-model="num1"
          class="inputs"
          type="number"
          aria-label="First number"
          aria-selected="true"
          tabindex="0"
        />
        <span class="operator">+</span>
        <input
          v-model="num2"
          class="inputs"
          type="number"
          aria-label="Second number"
          aria-selected="true"
          tabindex="1"
        />
        <span class="operator">=</span>
        <!-- Display the variable sum  -->
        <span class="operator">{{ sum || 0 }}</span>
      </form>
      <section class="buttons">
        <!-- Fire the add function on click  -->
        <button
          @click="add(this.num1, this.num2)"
          aria-label="Add numbers"
          aria-selected="true"
          tabindex="3"
        >
          Add It Up!
        </button>
        <!-- Fire the clear function on click  -->
        <button
          @click="clear()"
          aria-label="Clear numbers"
          aria-selected="true"
          tabindex="4"
        >
          Clear
        </button>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      // Declare necessary variables
      // Default both numbers to null for a better UX on first input
      num1: null,
      num2: null,
      sum: 0
    };
  },
  methods: {
    // Function add() adds up both variables after converting them into integers
    add(num1, num2) {
      this.sum = parseInt(num1) + parseInt(num2);
    },
    // Function clear() reset the variable & sum to null
    clear() {
      this.sum = 0;
      this.num1 = null;
      this.num2 = null;
    }
  }
};
</script>

<style>
/* General Styling */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #18776e;
}
body {
  margin: 0;
  box-sizing: border-box;
}
.wrapper {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: rgb(170, 168, 168);
}

/* Calculator Styles */
.calculator {
  margin-top: -100px;
  background: whitesmoke;
  height: 375px;
  width: 700px;
  border-radius: 15px;
  border: 3px solid #18776e;
  display: flex;
  flex-direction: column;
  box-shadow: 0px 10px 13px -7px #2b2a2a, 5px 5px 15px 5px rgba(0, 0, 0, 0);
}
.calculator h1 {
  font-size: 3rem;
  margin: 50px auto;
  text-align: center;
  text-shadow: 2px 2px 3px #807d7c;
}
.operation {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  height: 100%;
}
.buttons {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  height: 100%;
}
button {
  width: 170px;
  border: 3px solid #18776e;
  padding: 7px 12px;
  font-size: 1.7rem;
  color: #18776e;
  border-radius: 15px;
  box-shadow: 2px 2px 6px 0px #858484, 5px 5px 5px 5px rgba(0, 0, 0, 0);
}
button:hover {
  color: white;
  background-color: #18776e;
  cursor: pointer;
  box-shadow: inset -1px 3px 8px 1px #b6d3d0, 2px 5px 6px 0px #2b2a2a,
    5px 5px 15px 5px rgba(0, 0, 0, 0);
}
button:focus {
  outline: none !important;
  border: 5px solid #18776e;
  box-shadow: 0 0 10px #18776e;
}
.operator {
  font-size: 4rem;
  font-weight: bolder;
  text-shadow: 2px 2px 3px #807d7c;
}
.inputs {
  border: 3px solid #18776e;
  height: 50px;
  max-width: 120px;
  text-align: center;
  font-size: 2rem;
  color: #18776e;
  border-radius: 15px;
  text-shadow: 2px 2px 3px #807d7c;
}
.inputs:focus {
  outline: none !important;
  border: 5px solid #18776e;
  box-shadow: 0 0 10px #18776e;
}
/* Remove arrows inside input element  */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>
