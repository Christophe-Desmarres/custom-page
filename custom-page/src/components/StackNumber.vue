<template>
  <main>
  <ul class="infoGraphic"> 
    <li>
      <div class="numberWrap">
        <div class="number fontColor1">1</div>
        <div class="coverWrap">
          <div class="numberCover"></div>
        </div>
      </div>
      <div class="content">
        <div class="icon iconCodepen"></div>
        <h2>Develop</h2>
        <p>Sagittis, audantium sem eveniet lacus pede porttitor aenean.</p>
      </div>
    </li>
    <li>
      <div class="numberWrap">
        <div class="number fontColor2">2</div>
        <div class="coverWrap">
          <div class="numberCover"></div>
        </div>
      </div>
      <div class="content">
        <div class="icon iconSocial"></div>
        <h2>Engage</h2>
        <p>Sagittis, audantium sem eveniet lacus pede porttitor aenean.</p>
      </div>
    </li>
    <li>
      <div class="numberWrap">
        <div class="number  fontColor3">3</div>
        <div class="coverWrap">
          <div class="numberCover"></div>
        </div>
      </div>
      <div class="content">
        <div class="icon iconAirplane"></div>
        <h2>Deliver</h2>
        <p>Sagittis, audantium sem eveniet lacus pede porttitor aenean.</p>
      </div>
    </li>
    <li>
      <div class="numberWrap">
        <div class="number  fontColor4">4</div>
        <div class="coverWrap">
          <div class="numberCover"></div>
        </div>
      </div>
      <div class="content">
        <div class="icon iconMap"></div>
        <h2>Plan</h2>
        <p>Sagittis, audantium sem eveniet lacus pede porttitor aenean.</p>
      </div>
    </li>
    <li>
      <div class="numberWrap">
        <div class="number  fontColor5">5</div>
        <div class="coverWrap">
          <div class="numberCover"></div>
        </div>
      </div>
      <div class="content">
        <div class="icon iconBulb"></div>
        <h2>Educate</h2>
        <p>Sagittis, audantium sem eveniet lacus pede porttitor aenean.</p>
      </div>
    </li>
    <!--     <li>
      <div class="numberWrap">
      <div class="number  fontColor6">6</div>
      <div class="coverWrap">
        <div class="numberCover"></div>
      </div>
        </div>
      <div class="content">
        <div class="icon iconPeace"></div>
        <h2>Succeed</h2>
        <p>Sagittis, audantium sem eveniet lacus pede porttitor aenean.</p>
      </div>
    </li> -->
  </ul>

  
  <div class="controls">
      <div class="sliderBox">
          <input id="range" type="range" name="font-size" min=".6" max="1.5" value="1" step=".1" data-units="rem" />
          <div>Scale in rems: <span class="range-value"></span></div>
        </div>
    </div>
    
</main>
</template>

<script>
// source : https://codepen.io/EricPorter/pen/GRvMEQP

export default {

}
</script>

<style lang="sass" scoped>

:root {
  // Scale is using this font-size
  --font-size: 0.8em;

  --bg1: #f5f8f7;
  --blue: #3498db;
  --green: #2ecc71;
  --purple: #9b59b6;
  --gold: #f1c40f;
  --red: #e74c3c;
  --orange: #e67e22;
  --shadow1: 0 2px 4px #00000026, 0 3px 6px #0000001f;
  --shadow2: 0 2px 6px #00000044, 0 4px 7px #00000022;
}

main {
  padding: 2vw;
}

ul.infoGraphic {
  // Resize with Ems
  font-size: var(--font-size);
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  li {
    position: relative;
    width: 100%;
    max-width: 25em;
    background: var(--bg1);
    border-radius: 0.5em;
    padding: 0.5em;
    z-index: 1;
    transition: all 0.2s;
    cursor: pointer;
    
    .numberWrap {
      position: absolute;
    }
    .number {
      font-family: "maven pro", sans-serif;
      font-size: 13em;
      font-weight: 900;
      width: 0.9em;
      text-align: center;
      &.fontColor1 {
        color: var(--blue);
      }
      &.fontColor2 {
        color: var(--green);
      }
      &.fontColor3 {
        color: var(--purple);
      }
      &.fontColor4 {
        color: var(--gold);
      }
      &.fontColor5 {
        color: var(--red);
      }
      &.fontColor6 {
        color: var(--orange);
      }
    }
    .coverWrap {
      transform: rotate(130deg);
      position: absolute;
      width: 18em;
      height: 15em;
      left: -3em;
      top: -1em;
      .numberCover {
        position: absolute;
        background: var(--bg1);
        width: 18em;
        height: 6em;
        border-radius: 50% 50% 0 0;
        border-bottom: 3px solid #f5f8f7;
        transition: all 0.4s;

        &::before {
          position: absolute;
          content: "";
          bottom: 5px;
          left: 4em;
          right: 4em;
          top: 5em;
          box-shadow: 0 0 30px 17px #48668577;
          border-radius: 100px / 10px;
          z-index: -1;
        }
        &::after {
          position: absolute;
          bottom: 0;
          content: "";
          left: -10%;
          width: 120%;
          height: 150%;
          background: radial-gradient(
            at bottom,
            #48668533,
            transparent,
            transparent
          );
          z-index: 1;
        }
      }
    }
    .content {
      margin: 8em 3em 1em 7em;
      position: relative;
      h2 {
        font-size: 1.7em;
        font-weight: 500;
        text-align: center;
        margin-bottom: 10px;
        text-transform: uppercase;
      }
      p {
        line-height: 1.5em;
      }
    }
  }
}

// I like the curved version too, so I made it a hover for fun.
ul.infoGraphic li:hover .coverWrap .numberCover {
  border-radius: 100%;
}


/////////////////////////////////////
// Fontawesome Icons
// List: http://astronautweb.co/snippet/font-awesome/

.icon {
  position: absolute;
  font-size: 2rem;
  text-align: center;
  top: -1.3em;
  left: 50%;
  transform: translatex(-50%);
  &:before {
    color: #666;
    font-family: FontAwesome;
    font-style: normal;
    font-weight: normal;
    text-decoration: inherit;
  }
}

.iconCodepen {
  &:before {
    content: "\f1cb";
  }
}

.iconSocial {
  &:before {
    content: "\f08a";
  }
}

.iconAirplane {
  &:before {
    content: "\f1d9";
  }
}

.iconMap {
  &:before {
    content: "\f278";
  }
}

.iconBulb {
  &:before {
    content: "\f0eb";
  }
}

.iconPeace {
  &:before {
    content: "\f25b";
  }
}

// --------------
// General Layout
// --------------

@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500&display=swap");

@import url("https://fonts.googleapis.com/css2?family=Maven+Pro:wght@800&display=swap");

html {
  height: 100%;
  box-sizing: border-box;
}
*,
*:before,
*:after {
  box-sizing: inherit;
}
body {
  font-family: "Poppins", sans-serif;
  background: var(--bg1);
  min-height: 100vh;
  color: #444; 
  display: grid;
  place-items: center;
  padding: 3rem 1rem 10em;
}

///////////////////////
// Controls

.controls {
    position: fixed;
    z-index: 2;
    bottom: 0;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    background: #d7d7d7a1;
    padding: .5rem 2em;
    border-top-right-radius: 1rem;
    border-top-left-radius: 1rem;
    border: 1px solid #0000004d;
}

.sliderBox {
  text-align: center;
  .range-value {
    font-weight: 500;
    font-size: 22px;
  }
}

input[type="range"] {
  width: 100%;
  margin: 1em 0;
  -webkit-appearance: none;
}
input[type="range"]:focus {
  outline: none;
}
input[type="range"]::-webkit-slider-runnable-track {
  background: #00000066;
  border: 0;
  border-radius: 1.3px;
  width: 100%;
  height: 2px;
  cursor: pointer;
}
input[type="range"]::-webkit-slider-thumb {
  margin-top: -10px;
  width: 20px;
  height: 20px;
  background: #eee;
  box-shadow: inset 0px 1px 1px #ffffff66, 0px 1px 3px rgba(0, 0, 0, 1);
  border: 1px solid rgba(0, 0, 0, 0);
  border-radius: 50px;
  cursor: pointer;
  -webkit-appearance: none;
}
input[type="range"]:focus::-webkit-slider-runnable-track {
  background: #eee;
}
input[type="range"]::-moz-range-track {
  background: #000;
  border: 0;
  border-radius: 1.3px;
  width: 100%;
  height: 1px;
  cursor: pointer;
}
input[type="range"]::-moz-range-thumb {
  width: 25px;
  height: 25px;
  background: #151728;
  border: 1px solid rgba(0, 0, 0, 0);
  border-radius: 50px;
  cursor: pointer;
}
input[type="range"]::-ms-track {
  background: transparent;
  border-color: transparent;
  border-width: 13px 0;
  color: transparent;
  width: 100%;
  height: 1px;
  cursor: pointer;
}
input[type="range"]::-ms-fill-lower {
  background: #151728;
  border: 0;
  border-radius: 2.6px;
}
input[type="range"]::-ms-fill-upper {
  background: #151728;
  border: 0;
  border-radius: 2.6px;
}
input[type="range"]::-ms-thumb {
  width: 25px;
  height: 25px;
  background: #151728;
  border: 1px solid rgba(0, 0, 0, 0);
  border-radius: 50px;
  cursor: pointer;
  margin-top: 0px;
  /*Needed to keep the Edge thumb centred*/
}
input[type="range"]:focus::-ms-fill-lower {
  background: #ffffff;
}
input[type="range"]:focus::-ms-fill-upper {
  background: #ffffff;
}

</style>