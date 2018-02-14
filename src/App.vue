<template>
  <div id="app">
    <div class="ui padded segment">
      <h2 class="ui header">Shape</h2>
      <p>A shape is a three dimensional object including any flat content as a side.</p>
      <vue-semantic-ui-shape ref="shapes">
        <div class="sides">
          <div class="side">
            <div class="ui card">
              <div class="image">
                <img src="http://semantic-ui.com/images/avatar/large/steve.jpg">
              </div>
              <div class="content">
                <div class="header">Steve Jobs</div>
              </div>
            </div>
          </div>
          <div class="side">
            <div class="ui card">
              <div class="image">
                <img src="http://semantic-ui.com/images/avatar/large/stevie.jpg">
              </div>
              <div class="content">
                <div class="header">Stevie Feliciano</div>
              </div>
            </div>
          </div>
           <div class="side">
            <div class="ui card">
              <div class="image">
                <img src="http://semantic-ui.com/images/avatar/large/steve.jpg">
              </div>
              <div class="content">
                <div class="header">Steve Works</div>
              </div>
            </div>
          </div>
        </div>
      </vue-semantic-ui-shape>
      <div class="ui hidden clearing divider"></div>
      <div class="ui icon buttons">
        <button class="ui button" @click="flipLeft('shapes')">
          <i class="left chevron icon"></i>
        </button>
        <button class="ui button" @click="flipUp('shapes')">
          <i class="up chevron icon"></i>
        </button>
        <button class="ui button" @click="flipDown('shapes')">
          <i class="down chevron icon"></i>
        </button>
        <button class="ui button" @click="flipRight('shapes')">
          <i class="right chevron icon"></i>
        </button>
      </div>
      <div class="ui icon buttons">
        <div class="ui button" @click="flipBack('shapes')"><i class="retweet icon"></i></div>
        <div class="ui button" @click="flipOver('shapes')"><i class="flipped retweet icon"></i></div>
      </div>
    </div>
    <div class="ui padded segment">
      <h2>Cube</h2>
      <p>A cube shape is formatted so that each side is the face of a cube</p>
      <vue-semantic-ui-shape class="cube" ref="cubes">
        <div class="sides">
          <div class="side">
            <div class="content">
              <div class="center">
                1
              </div>
            </div>
          </div>
          <div class="side">
            <div class="content">
              <div class="center">
                2
              </div>
            </div>
          </div>
          <div class="side">
            <div class="content">
              <div class="center">
                3
              </div>
            </div>
          </div>
          <div class="side">
            <div class="content">
              <div class="center">
                4
              </div>
            </div>
          </div>
        </div>
      </vue-semantic-ui-shape>
      <div class="ui hidden clearing divider"></div>
      <div class="ui icon buttons">
        <button class="ui button" @click="flipLeft('cubes')">
          <i class="left chevron icon"></i>
        </button>
        <button class="ui button" @click="flipUp('cubes')">
          <i class="up chevron icon"></i>
        </button>
        <button class="ui button" @click="flipDown('cubes')">
          <i class="down chevron icon"></i>
        </button>
        <button class="ui button" @click="flipRight('cubes')">
          <i class="right chevron icon"></i>
        </button>
      </div>
      <div class="ui icon buttons">
        <div class="ui button" @click="flipBack('cubes')"><i class="retweet icon"></i></div>
        <div class="ui button" @click="flipOver('cubes')"><i class="flipped retweet icon"></i></div>
      </div>
    </div>
    <div class="ui padded segment">
      <h2>Form</h2>
      <p>A form shape is formatted to allow for sides of form to be displayed</p>
      <vue-semantic-ui-shape class="form" ref="form">
        <div class="sides">
          <div class="ui side">
            <form class="ui form" style="height:241px;width:219px;">
              <div class="field">
                <label>First Name</label>
                <input style="height:38px;width:219px;" type="text" name="first-name" placeholder="First Name">
              </div>
              <div class="field">
                <label>Last Name</label>
                <input style="height:38px;width:219px;" type="text" name="last-name" placeholder="Last Name">
              </div>
              <div class="field">
                <div class="ui checkbox">
                  <input style="height:38px;width:219px;" type="checkbox" tabindex="0" class="hidden">
                  <label>I agree to the Terms and Conditions</label>
                </div>
              </div>
              <button class="ui button" type="submit">Submit</button>
            </form>
          </div>
          <div class="ui side">
            <div class="ui form" style="height:75px;width:568px;">
              <div class="fields">
                <div class="field">
                  <label>First name</label>
                  <input style="height:38px;width:219px;" type="text" placeholder="First Name">
                </div>
                <div class="field">
                  <label>Middle name</label>
                  <input style="height:38px;width:219px;" type="text" placeholder="Middle Name">
                </div>
                <div class="field">
                  <label>Last name</label>
                  <input style="height:38px;width:219px;" type="text" placeholder="Last Name">
                </div>
              </div>
            </div>
          </div>
        </div>
      </vue-semantic-ui-shape>
      <div class="ui hidden clearing divider"></div>
      <div class="ui icon buttons">
        <button class="ui button" @click="flipLeft('form')">
          <i class="left chevron icon"></i>
        </button>
        <button class="ui button" @click="flipUp('form')">
          <i class="up chevron icon"></i>
        </button>
        <button class="ui button" @click="flipDown('form')">
          <i class="down chevron icon"></i>
        </button>
        <button class="ui button" @click="flipRight('form')">
          <i class="right chevron icon"></i>
        </button>
      </div>
      <div class="ui icon buttons">
        <div class="ui button" @click="flipBack('form')"><i class="retweet icon"></i></div>
        <div class="ui button" @click="flipOver('form')"><i class="flipped retweet icon"></i></div>
      </div>
    </div>
    <div class="ui padded segment">
      <h2>Text</h2>
      <p>A text shape is formatted to allow for sides of text to be displayed</p>
      <vue-semantic-ui-shape class="text" ref="text">
        <div class="sides">
          <div class="ui header side active">Did you know? This side starts visible.</div>
          <div class="ui header side">Help, its another side!</div>
          <div class="ui header side">This is the last side</div>
        </div>
      </vue-semantic-ui-shape>
      <div class="ui hidden clearing divider"></div>
      <div class="ui icon buttons">
        <button class="ui button" @click="flipLeft('text')">
          <i class="left chevron icon"></i>
        </button>
        <button class="ui button" @click="flipUp('text')">
          <i class="up chevron icon"></i>
        </button>
        <button class="ui button" @click="flipDown('text')">
          <i class="down chevron icon"></i>
        </button>
        <button class="ui button" @click="flipRight('text')">
          <i class="right chevron icon"></i>
        </button>
      </div>
      <div class="ui icon buttons">
        <div class="ui button" @click="flipBack('text')"><i class="retweet icon"></i></div>
        <div class="ui button" @click="flipOver('text')"><i class="flipped retweet icon"></i></div>
      </div>
    </div>
  </div>
</template>

<script>
import VueSemanticUiShape from './components/VueSemanticUiShape.vue';
export default {
  name: 'app',
  components: {
    VueSemanticUiShape
  },
  methods: {
    flipOver(ref){
      this.$refs[ref].flipOver();
    },
    flipBack(ref){
      this.$refs[ref].flipBack();
    },
    flipLeft(ref){
      this.$refs[ref].flipLeft();
    },
    flipRight(ref){
      this.$refs[ref].flipRight();
    },
    flipUp(ref){
      this.$refs[ref].flipUp();
    },
    flipDown(ref){
      this.$refs[ref].flipDown();
    }
  }
}
</script>