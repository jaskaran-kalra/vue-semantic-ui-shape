
# vue-semantic-ui-shape
Semantic UI Shape built using Vue js. This plugin uses semantic ui css and Vue js (no jQuery). This plugin contains only semantic ui shape. For other components search for vue-semantic-ui-{component-name}

# How to use it

## Installation

### NPM
Ubuntu / Mac
```bash
$ npm install vue-semantic-ui-shape
```
Windows
```cmd
c:\path\to\project\folder> npm install vue-semantic-ui-shape
```

### CommonJS
```js
var VueSemanticUiShape = require('vue-semantic-ui-shape').VueSemanticUiShape;

new Vue({
  components: {
    'vue-semantic-ui-shape': VueSemanticUiShape
  }
})
```

### ES6
```js
import VueSemanticUiShape from 'vue-semantic-ui-shape'

new Vue({
  components: {
    'vue-semantic-ui-shape': VueSemanticUiShape
  }
})
```

#Variable Shapes
import VueSemanticUiShape from 'vue-semantic-ui-shape'
paste your sides between vue-semantic-ui-shape's opening and closing tags.
```html

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
  </div>
</vue-semantic-ui-shape>
```

#Cubes
import VueSemanticUiShape from 'vue-semantic-ui-shape'
paste your sides between vue-semantic-ui-shape's opening and closing tags.
```html

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
  </div>
</vue-semantic-ui-shape>
```

#Form
import VueSemanticUiShape from 'vue-semantic-ui-shape'
paste your sides between vue-semantic-ui-shape's opening and closing tags.
```html

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
```

#Text
import VueSemanticUiShape from 'vue-semantic-ui-shape'
paste your sides between vue-semantic-ui-shape's opening and closing tags.
```html

<vue-semantic-ui-shape class="text" ref="text">
  <div class="sides">
    <div class="ui header side active">Did you know? This side starts visible.</div>
    <div class="ui header side">Help, its another side!</div>
    <div class="ui header side">This is the last side</div>
  </div>
</vue-semantic-ui-shape>
```

### Browser globals
The `dist` folder contains `vue-semantic-ui-shape.min.js`

```html
<body>
  <div id="app">
    <vue-semantic-ui-shape></vue-semantic-ui-shape>
  </div>
  <script src="path/to/vue.js"></script>
  <script type="text/javascript" src="path/to/vue-semantic-ui-shape.js"></script>
  <script type="text/javascript">
    Vue.use(VueSemanticUiShape);
  </script>
</body>
```

## Local setup

```
npm install
npm run dev
```

Call component methods to change the shape.

Props
```html
1. start - from which (zero based) index the shape should start. (default 0);
e.g. <vue-semantic-ui-shape :start="1"></vue-semantic-ui-shape>
```

Methods
```html
this.$refs[`ref`].flipOver();
this.$refs[`ref`].flipBack();
this.$refs[`ref`].flipLeft();
this.$refs[`ref`].flipRight();
this.$refs[`ref`].flipUp();
this.$refs[`ref`].flipDown();
```

## Examples
https://github.com/jaskaran-kalra/vue-semantic-ui-shape/blob/master/src/App.vue


## License

vue-semantic-ui-shape is licensed under [The MIT License](LICENSE).

