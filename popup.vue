<template>
  <div>
    <h2 class="text-center">
      Welcome to your
      <a href="https://www.plasmo.com" target="_blank">Plasmo</a> Extension!
    </h2>

    <div class="container">
      <QBtn @click="decrement">-</QBtn>
      <p>
        <b>{{ state.count }}</b>
      </p>
      <QBtn @click="increment">+</QBtn>
    </div>
  </div>
  <p v-if="state.action" class="action text-center">
    {{ state.action }}
  </p>

  <a href="https://docs.plasmo.com" target="_blank">
    <QChip>View Docs</QChip>
  </a>
</template>

<style>

.container {
  min-width: 470px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 47px;
}

.text-center {
  text-align: center;
}

.action {
  color: #470;
  font-weight: bold;
}
</style>
<script lang="ts" setup>
import type {PlasmoGetStyle} from "plasmo";
import {QBtn, QChip, Quasar} from "quasar";
import cssText from "quasar/src/css/index.sass";
import type {App} from "vue"
import {reactive} from "vue";


const state = reactive({count: 0, action: null})

const getStyle: PlasmoGetStyle = () => {
  const style = document.createElement("style");

  // Append your existing CSS text
  style.textContent = cssText;


  return style;
};


function increment() {
  state.count++
  state.action = "increment"
}

function decrement() {
  state.count--
  state.action = "decrement"
}


defineOptions({
  prepare(app: App) {

    app.use(Quasar, {});
  },
});
</script>


