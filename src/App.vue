<script setup>
import ChildComponent from "./components/ChildComponent.vue"
import Test1 from "./Test1.vue";
import Test2 from "./Test2.vue";
import Test3 from "./Test3.vue";
import Test4 from "./Test4.vue";
import Test5 from "./Test5.vue";
import {ref} from "vue";

const counter = ref(0);
</script>

<template>
  <header>
    <div>
      <h1>
        case 1 (works properly)
      </h1>
      <Test1/>
    </div>
    <div>
      <h1>
        case 2
      </h1>
      <Test2/>
    </div>
    <div>
      <h1>
        case 3
      </h1>
      <Test3/>
    </div>
    <div>
      <h1>
        case 4
      </h1>
      <Test4/>
    </div>
    <div>
      <h1>
        case 5
      </h1>
      <Test5/>
    </div>
  </header>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
