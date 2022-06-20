<template>
  <div class="background">
    <img src="./assets/background.png" alt="" />
  </div>
  <div class="logo">
    Autonomy <br />
    Capital
  </div>
  <div id="menuToggle">
    <input type="checkbox" />

    <span></span>
    <span></span>
    <span class="lst-span"></span>

    <ul id="menu"></ul>
  </div>
  <div class="layout">
    <div class="head-text item1">
      <h2>Leadership</h2>
      <p>
        We believe the successful management of macro investment strategies
        requires strong leadership guided by values that not only safeguard the
        best interests of our partners, but also empower our people to deliver
        exceptional results.
      </p>
    </div>
    <div
      id="carouselExampleDark"
      class="carousel carousel-dark slide"
      data-bs-ride="carousel"
    >
      <div class="carousel-inner">
        <div
          class="carousel-item"
          v-for="(SlideContent, index) in SlideContents"
          :key="'SlideContent-' + SlideContent.id"
          :class="{ 'carousel-item': true, active: index === active }"
        >
          <div class="carousel-align">
            <div>
              <img :src="SlideContent.img" alt="jjjj" />
            </div>
            <div class="txt-desc">
              <h5>{{ SlideContent.name }}</h5>
              <h6>{{ SlideContent.position }}</h6>
              <p>{{ SlideContent.description }}</p>
              <p>{{ SlideContent.description2 }}</p>
            </div>
          </div>
        </div>

        <div class="carousel-indicators">
          <button
            type="button"
            class="indicator-btn"
            v-for="(SlideContent, index) in SlideContents"
            :key="'SlideContent-' + SlideContent.id"
            :class="{ active: index === active }"
            data-bs-target="#carouselExampleDark"
            :data-bs-slide-to="index"
            @click="setActive((active = index))"
          ></button>
        </div>

        <button
          class="next-btn-left"
          type="button"
          data-bs-target="#carouselExampleDark"
          data-bs-slide="prev"
          @click="setActive(active - 1)"
          v-if="active !== 0"
        >
          <i class="carousel-control-prev-icon blue" aria-hidden="true"></i>
        </button>
        <button
          class="next-btn-right"
          @click="setActive(active + 1)"
          type="button"
          data-bs-target="#carouselExampleDark"
          data-bs-slide="next"
          v-if="active !== total"
        >
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Next</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      SlideContents: [
        {
          img: require("./assets/Guy2.png"),
          name: "Robert Gibbons",
          position: "Partner, Founder and Chief Investment Officer",
          description:
            "For over 25 years, Robert Gibbins has applied his fascination with the development and transition of economies and societiesto the management of global macro investment strategies  adistinctive focus that has personified Autonomy since its inception.",
          description2:
            " After earning a BS in Economics from the Wharton School at the University of Pennsylvania, Robert began his career at JP Morgan in 1992. He subsequently traded northern European FX and interest rates at Lehman Brothers for two years, followed by seven years as head of emerging markets and global macro proprietary trading.",
        },
        {
          name: "Ivan Ritossa",
          img: require("./assets/Guy1.png"),
          position: "Chief Executive Officer",
          description:
            "Ivan has over 35 years of experience in the global financial services industry, building a rich diversity of businesses. He was previously an MD and a member of the executive committee at Barclays Capital, MD at Lehman Brothers, and a partner and senior MD at Bankers Trust. ",
          description2:
            "Ivan earned a Bachelor of Commerce (honors) degree, majoring in Finance, from the University of New South Wales, Australia. He has served on the New York Federal Reserve Foreign Exchange Committee, the Bank of England Foreign Exchange Joint Standing Committee, and the Singapore Foreign Exchange Markets Committee.",
        },
        {
          name: "James Bond",
          img: require("./assets/avatar.jpg"),
          position: "Position at institute",
          description:
            "Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ad eos unde porro neque sequi iusto pariatur veritatis iste, alias necessitatibus similique repellendus qui temporibus adipisci odio, veniam maxime, molestias sed. Lorem ipsum, dolor sit amet consectetur adipisicing elit. Qui quisquam dolor, eum distinctio optio ex eius obcaecati nam non doloribus minima pariatur fugiat numquam ratione omnis, excepturi itaque delectus quas! Lorem, ipsum dolor sit amet consectetur adipisicing elit. Ipsa ducimus, natus aspernatur animi accusamus commodi molestias explicabo perspiciatis rem corporis veniam architecto ipsum illum, eum sapiente atque necessitatibus! Aperiam, reiciendis.",
          description2: "",
        },
      ],
      active: 0,
    };
  },
  methods: {
    setActive(index) {
      let active = index;

      if (index === this.SlideContents.length) active = 0;
      else if (index === -1) active = this.SlideContents.length - 1;

      this.active = active;
    },
  },
  computed: {
    total() {
      return this.SlideContents.length - 1;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Anek+Latin:wght@100&family=Bitter:wght@300&family=Inconsolata:wght@300&family=Karma:wght@300&display=swap");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
body {
  overflow-x: hidden;
}
.blue {
  color: blue;
}
#menuToggle {
  display: block;
  position: fixed;
  top: 50px;
  right: 50px;

  z-index: 1;

  -webkit-user-select: none;
  user-select: none;
}
.logo {
  position: fixed;
  top: 50px;
  left: 80px;
  font-size: 25px;
  color: white;
  font-family: "Courier New", Courier, monospace;
  font-weight: 50;
  text-align: start;
}
#menuToggle input {
  display: block;
  width: 40px;
  height: 32px;
  position: absolute;
  top: -7px;
  left: -5px;

  cursor: pointer;

  opacity: 0;
  z-index: 2;

  -webkit-touchallout: none;
}

#menuToggle span {
  display: block;
  width: 30px;
  height: 3px;
  margin-bottom: 5px;
  position: relative;

  background: #5a6a81;

  z-index: 1;

  transform-origin: 4px 0px;

  transition: transform 0.5s cubic-bezier(0.77, 0.2, 0.05, 1),
    background 0.5s cubic-bezier(0.77, 0.2, 0.05, 1), opacity 0.55s ease;
}

#menuToggle span:first-child {
  transform-origin: 0% 0%;
}

#menuToggle span:nth-last-child(2) {
  transform-origin: 0% 100%;
}

#menuToggle input:checked ~ span {
  opacity: 1;
  transform: rotate(45deg) translate(-2px, -1px);
  background: #5d8fff;
}

#menuToggle input:checked ~ span:nth-last-child(3) {
  opacity: 0;
  transform: rotate(0deg) scale(0.2, 0.2);
}

#menuToggle input:checked ~ span:nth-last-child(2) {
  transform: rotate(-45deg) translate(0, -1px);
}

.background img {
  position: fixed;
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
  opacity: 0.2;
  object-fit: cover;
}
.txt-desc p {
  font-size: 20px;
  font-weight: 900;
}
.txt-desc h5 {
  color: #507ad5;
  font-weight: bolder;
}
.txt-desc h6 {
  color: #507ad5;
  font-weight: 700;
}
.txt-desc {
  width: 300px;
  height: 400px;
  text-align: left;
  font-family: "Anek Latin", sans-serif;
}
.background {
  position: fixed;
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
  z-index: -1;
  background-color: #262b38;
}
.bi-chevron-left {
  color: black;
}
.carousel {
  height: 100%;
}
.carousel-indicators {
  width: fit-content;
  margin: 0% !important;
  left: 60%;
  top: 70%;
  height: fit-content;
}
.carousel-indicators .indicator-btn {
  right: 0;
  height: 10px;
  width: 10px;
  border-radius: 50%;
  background-color: #5d8fff !important;
}
.bi-chevron-right {
  color: black;
}
.carousel-align {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.head-text {
  width: 300px;
  text-align: left;
  padding-left: 80px;
}
.head-text p {
  color: white;
  font-family: "Anek Latin", sans-serif;
  padding-top: 55px;
  font-size: 15px;
}
.head-text h2 {
  color: #507ad5;
  font-size: 40px;
  font-family: "Anek Latin", sans-serif;
}
.layout {
  position: absolute;
  top: 35%;
  display: grid;
  grid-template-columns: 1fr 2fr;
  width: 100%;
}

.next-btn-left {
  position: absolute;
  top: 80%;
  left: 50%;
  border: none;
  background-color: transparent;
  color: #507ad5 !important;
}

.next-btn-right {
  position: absolute;
  top: 80%;
  left: 70%;
  border: none;
  background-color: transparent;
}
.carousel-control-prev-icon {
  width: 25px;
  height: 18px;
}
.carousel-control-next-icon {
  width: 25px;
  height: 18px;
}
.name {
  position: absolute;
  left: 70%;
  top: 80%;
}
.carousel-item p {
  font-size: 12px;
}
.carousel-item img {
  height: 300px;
  width: 300px;
  border-radius: 50%;
  background-color: white;
  padding: 30px;
  box-shadow: inset 0 2px 1px rgba(0, 0, 0, 0.2);
}
/* Media queries */
@media screen and (max-width: 900px) {
  .layout {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    top: 15%;
  }
  .background {
    width: 100%;
  }
  .carousel {
    margin-top: 50px;
  }
  .background img {
    width: 100%;
  }
  .carousel-item img {
    margin-right: 40px;
    margin-left: 20px;
  }
  .carousel-item p {
    color: white;
  }
  .head-text {
    width: 400px;
  }
  .head-text h2 {
    font-size: 50px;
    padding-top: 30px;
  }
  .head-text p {
    padding-top: 20px;
    font-size: 18px;
  }
  .logo {
    position: absolute;
  }
}
@media screen and (max-width: 680px) {
  .carousel-align {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  .carousel {
    width: 400px;
  }
  .txt-desc {
    text-align: center;
    padding-top: 60px;
  }
  .head-text {
    padding-left: 60px;
  }
  .carousel-indicators {
    top: 45%;
    left: 45%;
  }
  .next-btn-left {
    top: 45%;
    left: 22%;
  }
  .next-btn-right {
    top: 45%;
  }
}
</style>
