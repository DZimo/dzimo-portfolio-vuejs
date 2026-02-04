<script setup>
defineProps({
  msg: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <div class="greetings">
    <h1 class="primary">{{ msg }}</h1>
    <h3 style="margin-bottom: 1rem;">
      Native Application and Web developer with a Master degree i was always passionate about software development and
      graphic design.
    </h3>
    <span class="nav-item social-icons">
      <span class="fa-stack">
        <a href="https://www.linkedin.com/in/mohamed-nazim-belabed-b68799127/">
          <i class="fas fa fa-stack-2x"></i>
          <i class="fab fa-linkedin-in fa-stack-1x"></i>
        </a>
      </span>
      <span class="fa-stack">
        <a href="https://github.com/DZimo">
          <i class="fas fa fa-stack-2x"></i>
          <i class="fab fa-github fa-stack-1x"></i>
        </a>
      </span>
      <span class="fa-stack">
        <a href="https://play.google.com/store/apps/developer?id=ROBOTOP">
          <i class="fas fa fa-stack-2x"></i>
          <i class="fab fa-google-play fa-stack-1x"></i>
        </a>
      </span>
    </span>
    <h4 style="margin-top: 1rem;">
      C#: Unity, WPF, Avalonia, Blazor.
    </h4>
    <h4 style="margin-top: 1rem;">
      C/C++: Zephyr RTOS, PlatformIO, Arduino.
    </h4>
    <h4 style="margin-top: 1rem;">
      Other: JS, VueJS, CI/CD.
    </h4>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
