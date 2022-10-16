<template>
  <img
    class="vuetify-logo"
    alt="Vuetify Logo"
    src="https://images.cointelegraph.com/images/1200_aHR0cHM6Ly9zMy5jb2ludGVsZWdyYXBoLmNvbS9zdG9yYWdlL3VwbG9hZHMvdmlldy9mYmU4YjVjZjg3ODBhNmE1ZjZmZjM2NzhlNjBlZDM0OS5wbmc=.jpg"
  >
</template>

<style>
.vuetify-logo {
  height: 180px;
  /* width: 180px; */
  transform: rotateY(560deg);
  animation: turn 3.5s ease-out forwards 1s;
}

@keyframes turn {
  100% {
    transform: rotateY(0deg);
  }
}
</style>
