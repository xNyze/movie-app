<template>
  <button type="button" v-on:click="$emit('buttonClicked')">
    <transition name="fade" mode="out-in">
      <p class="btnName" :key="btnName">{{btnName}}</p>
    </transition>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    btnName: String
  }
};
</script>

<style>
button {
  width: 10vw;
  height: 5vh;
  border: none;
  border-radius: 0.5vh;
  border: 1px solid #000438;
  color: var(--white);
  background-color: var(--cyan);
  background-image: -webkit-linear-gradient(top, var(--lightblue), var(--lightblue));
  background-image: linear-gradient(to bottom, var(--lightblue), var(--darkblue));
  box-shadow: 0 1px 0 var(--lightgrey) inset,
    0 -1px 0 var(--lightgrey) inset, 0 1px 0 #4442ad,
    0 1px 2px var(--black);
}

button:hover {
  cursor: pointer;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.btnName {
  margin-top: 10px;
  font-size: 1em;
  text-align: center;
}
</style>
