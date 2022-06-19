<template>
  <div class="background"></div>
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
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum
        explicabo, veniam similique corrupti earum excepturi blanditiis quae
        repellendus iste alias reprehenderit distinctio aliquam, at nisi est
        ipsa labore et minima?
      </p>
    </div>
    <div
      id="carouselExampleDark"
      class="carousel carousel-dark slide"
      data-bs-ride="carousel"
    >
      <div class="carousel-inner">
        <div class="carousel-item active" data-bs-interval="10000">
          <div class="carousel-align">
            <div>
              <img src="https://picsum.photos/id/100/600/200" />
            </div>
            <div>
              <h5>First slide label</h5>
              <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Labore
                totam dicta at esse ipsum sapiente eligendi, beatae, tenetur et
                unde aspernatur odio, molestiae atque? Quam a velit accusamus
                sed deleniti!
              </p>
              <p class="name">Ivan Ritossa</p>
            </div>
          </div>
        </div>
        <div class="carousel-item" data-bs-interval="2000">
          <div class="carousel-align">
            <div>
              <img src="https://picsum.photos/id/121/600/200" />
            </div>
            <div>
              <h5>Second slide label</h5>
              <p>
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ad eos
                unde porro neque sequi iusto pariatur veritatis iste, alias
                necessitatibus similique repellendus qui temporibus adipisci
                odio, veniam maxime, molestias sed.
              </p>
            </div>
          </div>
        </div>
        <div class="carousel-item">
          <div class="carousel-align">
            <div>
              <img src="https://picsum.photos/id/125/600/200" alt="..." />
            </div>
            <div>
              <h5>Third slide label</h5>
              <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
                Corporis velit necessitatibus voluptatum iste provident ab,
                suscipit facere voluptatem? Repellat eligendi optio quia quo
                repellendus eos placeat cumque omnis debitis facilis!
              </p>
            </div>
          </div>
        </div>
        <div class="carousel-indicators">
          <button
            type="button"
            data-bs-target="#carouselExampleDark"
            data-bs-slide-to="0"
            class="active indicator-btn"
            aria-current="true"
            aria-label="Slide 1"
          ></button>
          <button
            type="button"
            class="indicator-btn"
            data-bs-target="#carouselExampleDark"
            data-bs-slide-to="1"
            aria-label="Slide 2"
          ></button>
          <button
            type="button"
            class="indicator-btn"
            data-bs-target="#carouselExampleDark"
            data-bs-slide-to="2"
            aria-label="Slide 3"
          ></button>
        </div>
        <button
          class="next-btn-left"
          type="button"
          data-bs-target="#carouselExampleDark"
          data-bs-slide="prev"
        >
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Previous</span>
        </button>
        <button
          class="next-btn-right"
          type="button"
          data-bs-target="#carouselExampleDark"
          data-bs-slide="next"
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
    return {};
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
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
#menuToggle input {
  display: block;
  width: 40px;
  height: 32px;
  position: absolute;
  top: -7px;
  left: -5px;

  cursor: pointer;

  opacity: 0; /* hide this */
  z-index: 2; /* and place it over the hamburger */

  -webkit-touch-callout: none;
}

/*
 * Just a quick hamburger
 */
#menuToggle span {
  display: block;
  width: 33px;
  height: 4px;
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

/* 
 * Transform all the slices of hamburger
 * into a crossmark.
 */
#menuToggle input:checked ~ span {
  opacity: 1;
  transform: rotate(45deg) translate(-2px, -1px);
  background: #5d8fff;
}

/*
 * But let's hide the middle one.
 */
#menuToggle input:checked ~ span:nth-last-child(3) {
  opacity: 0;
  transform: rotate(0deg) scale(0.2, 0.2);
}

/*
 * Ohyeah and the last one should go the other direction
 */
#menuToggle input:checked ~ span:nth-last-child(2) {
  transform: rotate(-45deg) translate(0, -1px);
}

/*
 * Make this absolute positioned
 * at the top left of the screen
 */
.background {
  position: fixed;
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
  z-index: -1;
  background-image: repeating-linear-gradient(
    44deg,
    rgb(0, 0, 0) 0px,
    #242e40 150px
  );
}
.bi-chevron-left {
  color: black;
}
.carousel {
  height: 100%;
}
.carousel-indicators {
  left: 50%;
  top: 65%;
}
.carousel-indicators .indicator-btn {
  height: 15px;
  width: 15px;
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
.carousel-align h5 {
  color: #507ad5;
}
.head-text p {
  color: white;
}
.head-text h2 {
  color: #507ad5;
  font-weight: 50;
}
.layout {
  margin-top: 25%;
  display: grid;
  grid-template-columns: 1fr 2fr;
}
.next-btn-left {
  border: none;
  background-color: transparent;
  position: sticky;
  top: 80%;
  left: 60%;
}
.next-btn-right {
  border: none;
  background-color: transparent;
  position: sticky;
  top: 80%;
  left: 85%;
}
.carousel-control-prev-icon {
  width: 25px;
  height: 25px;
}
.carousel-control-next-icon {
  width: 25px;
  height: 25px;
}
.name {
  position: absolute;
  left: 70%;
  top: 80%;
}
img {
  height: 300px;
  width: 300px;
  border-radius: 50%;
  background-color: white;
  padding: 30px;
}
</style>
