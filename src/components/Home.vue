<template>
  <div
    :class="{ 'bg-white': !nightMode, 'bg-dark': nightMode }"
    class="pt-5 p-st"
  >
    <div
      class="container"
      data-aos="fade"
      data-aos-once="true"
      data-aos-duration="1000"
    >
      <div class="row align-items-center">
        <div class="col-xl-6 col-bg-6 col-md-6 col-sm-12 text-center">
          <img style="width: 450px" :src="picture" />
        </div>
        <div class="col-xl-6 col-bg-6 col-md-6 col-sm-12 pt-5">
          <span
            class="home-title"
            :class="{ pgray: !nightMode, 'text-light': nightMode }"
          >
            Hi, I am Bongomin Daniel !
          </span>
          <div>
            <hr />
            <p></p>
            <p v-html="description"></p>
          </div>
          <div class="text-center pb-4">
            <div class="buttons">
              <a class="twitter" @click="open('github')"
              v-tooltip.bottom="'GitHub'">
              <i class="fab fa-linkedin"></i>
              </a>
              <a class="github" @click="open('github')"
              v-tooltip.bottom="'Github'"><i class="fab fa-github"></i></a>
              <a class="resume" @click="open('resume')"
              v-tooltip.bottom="'Resume'"><i class="fa fa-file"></i></a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import info from "../../info";

import Wave from "./helpers/Wave";

export default {
  name: "Home",
  components: {
    Wave,
  },
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      picture: info.flat_picture,
      description: info.description,
      name: info.name,
      linkedin: info.links.linkedin,
      github: info.links.github,
      behance: info.links.behance,
      resume: info.links.resume,
    };
  },
  methods: {
    open(link) {
      switch (link) {
        case "linkedin":
          window.open(this.linkedin, "_blank");
          break;
        case "github":
          window.open(this.github, "_blank");
          break;
        case "behance":
          window.open(this.behance, "_blank");
          break;
        case "resume":
          window.open(this.resume, "_blank");
          break;
      }
    },
  },
};
</script>

<style scoped>
.home-title {
  font-size: 32px;
  font-weight: 500;
}

img {
  max-width: 800px;
  max-height: 500px;
  margin-top: 80px;
  transform: rotateY(180deg);
}

@media only screen and (max-width: 580px) {
  img {
    object-fit: cover;
    border-radius: 50%;
    height: 200px;
    width: 200px;
    margin-top: 10px;
    margin-bottom: 10px;
    border: 2px solid rgb(205, 205, 205);
  }
}

.fa {
  font-size: 15px;
}

.btn {
  border-color: #759cc9;
  color: #759cc9;
}

.btn:hover {
  background-color: #759cc9;
  border-color: #759cc9;
  color: white;
}

.btn:focus {
  background-color: #759cc9;
  border-color: #759cc9;
  color: white;
}

.btn:focus {
  outline: none !important;
}

p {
  text-align: justify;
  font-weight: 400;
}

.buttons {
  margin-top: 40px;
}
.buttons a {
  margin-right: 30px;
  width: 64px;
  height: 64px;
  font-size: 24px;
  display: inline-block;
  position: relative;
  line-height: 64px;
  background-color: #eaeaea;
  background-image: linear-gradient(to bottom, #f6f6f6, #eaeaea);
  border-radius: 32px;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.25), 0 2px 3px rgba(0, 0, 0, 0.1);
}
.buttons a:active {
  top: 1px;
  background-image: linear-gradient(to bottom, #eaeaea, #f6f6f6);
}
.buttons a:active::before {
  top: -9px;
}
.buttons a::before {
  content: "";
  position: absolute;
  z-index: -1;
  top: -8px;
  right: -8px;
  bottom: -8px;
  left: -8px;
  background-color: #eaeaea;
  border-radius: 140px;
  opacity: 0.5;
}
:hover .buttons a::before {
  opacity: 1;
}

.twitter:hover::before {
  background-color: #c6f0f8;
}

.github:hover::before {
  background-color: #dae1f0;
}

.resume:hover::before {
  background-color: #fadae6;
}
/* LEAVES */
</style>
