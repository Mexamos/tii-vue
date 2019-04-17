<template>
  <div id="tii">
    <div id="test-interface-imitator-wrapeer" :class="togglePositionClass" v-show="visability">

      <div class="tii-header">
        <div class="tii-img-toggle-position-wrapper" @click="toggle_position = !toggle_position ? true : false">
          <img src="./assets/scroll-vertical-arrows.png" id="tii-img-toggle-position">
        </div>
        <div class="tii-roll-up-wrapper" title="Roll up plugin" @click="visability = false">
          <img src="./assets/roll-up.png" id="tii-roll-up">
        </div>
      </div>

      <div class="tii-body-wrapper">

        <div class="tii-include-input-wrapper">
          <label for="tii-include-elements">
            Include elements
          </label>
          <input type="text" name="tii-include-elements" id="tii-include-elements" placeholder="Enter selectors">
        </div>

        <div class="tii-exclude-input-wrapper">
          <label for="tii-exclude-elements">
            Exclude elements
          </label>
          <input type="text" name="tii-exclude-elements" id="tii-exclude-elements" placeholder="Enter selectors">
        </div>

        <div class="tii-exclude-block-input-wrapper">
          <label for="tii-exclude-blocks">
            Include elements
          </label>
          <input type="text" name="tii-exclude-blocks" id="tii-exclude-blocks" placeholder="Enter selectors">
        </div>

        <div class="tii-timers-wrapper">

          <div class="tii-interval-input-wrapper">
            <label for="tii-interval-input">
              Interval run listners
            </label>
            <input type="number" name="tii-interval-input" id="tii-interval-input" step="100">
            <div class="tii-format-time">
              ms
            </div>
          </div>
          
          <div class="tii-total-duration-input-wrapper">
            <label for="tii-total-duration-input">
              Total duration test
            </label>
            <input type="number" name="tii-total-duration-input" id="tii-total-duration-input" step="100">
            <div class="tii-format-time">
              ms
            </div>
          </div>

        </div>

      </div>

      <div class="tii-button-wrapper">
        <button class="tii-button">
          Start test
        </button>
      </div>

    </div>

    <div v-show="!visability" class="tii-expand" title="Expand plugin" @click="visability = true">
      <img src="./assets/expand.png" id="tii-img-expand">
    </div>
  </div>
</template>

<script>

import '@ulivz/get-event-listeners'

export default {
  name: 'app',
  data() {
    return {
      inner_element_listners: [],
      visability: true,
      toggle_position: true
    }
  },
  computed: {
    togglePositionClass() {
      if(this.toggle_position) return 'tii-right-position'
      else return 'tii-left-position'
    }
  },
  mounted() {
    console.log('window', window.getAllEventListeners())
  },
  methods: {

  }
}
</script>

<style scoped>
#tii {
  /* font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}

#test-interface-imitator-wrapeer {
    width: 280px;
    height: 260px;
    position: fixed;
    top: 30px;
    padding: 10px;
    border-radius: 1px;
    background: linear-gradient(45deg, rgb(13, 13, 13), 30%, rgb(72, 72, 72));
    box-shadow: 3px 3px 5px 2px rgba(0, 0, 0, 0.5);
    font-family: sans-serif;
    font-size: 14px;
    color: rgb(240, 248, 255);
    opacity: 0.6;
    transition: opacity .5s;
}
#test-interface-imitator-wrapeer:hover {
    opacity: 1;
}
#test-interface-imitator-wrapeer label {
    display: block;
}
.tii-left-position {
    left: 30px;
}
.tii-right-position {
    right: 30px;
}

.tii-expand {
    position: fixed;
    top: 40px;
    right: 0px;
    background: white;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 20px;
    border-radius: 1px;
    cursor: pointer;
    border: 1px solid #a1a1a1;
    border-right: unset;
}
#tii-img-expand {
    width: 15px;
    padding: 2.5px;
}

.tii-header {
    display: flex;
}
.tii-img-toggle-position-wrapper, .tii-roll-up-wrapper {
    background: white;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 30px;
    border-radius: 1px;
    cursor: pointer;
    border: 1px solid #a1a1a1;
}
.tii-img-toggle-position-wrapper:hover {
    box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
}
#tii-img-toggle-position {
    width: 20px;
    height: 20px;
}
#tii-roll-up {
    width: 15px;
    height: 12px;
}
.tii-roll-up-wrapper {
    position: absolute;
    right: 10px;
    padding: 4px;
    width: 15px;
}



.tii-body-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    height: 200px;
}

.tii-body-wrapper input {
    width: 250px;
}

.tii-body-wrapper > div:not(.tii-timers-wrapper) label {
    text-align: center;
}

.tii-timers-wrapper {
    display: flex;
    box-sizing: border-box;
    justify-content: space-between;
    width: 100%;
    padding: 0 15px;
}
.tii-interval-input-wrapper {

}
.tii-interval-input-wrapper input {
    width: 60px;
    float: left;
}

.tii-total-duration-input-wrapper input {
    width: 60px;
    float: left;
}
.tii-format-time {
    margin-top: 6px;
    margin-left: 3px;
    display: inline-block;
}

.tii-button-wrapper {
    display: flex;
    justify-content: center;
    margin-top: 10px;
}

.tii-element-with-listner:hover {
    box-shadow: 0px 0px 10px 5px #a142f4
}

</style>
