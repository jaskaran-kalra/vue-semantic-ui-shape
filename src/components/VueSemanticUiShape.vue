<template>
  <div class="ui shape"><slot></slot></div>
</template>
<script>
  export default {
    props: ['start'],
    data () {
      return {
        prevIndex: 0,
        index: 0,
        sidesEl: '',
        sides: [],
        nextDirs: ['down','right','flip-right'],
        prevDirs: ['up','left','flip-left'],
        shapeDim: {
          h: 0,
          w: 0,
        },
        curDir: '',
        hHalf: 0,
        wHalf: 0,
        flipMode: false,
        animating: false,
        sidesDim: []
      }
    },
    computed: {
      totalSides(){
        return this.sides.length;
      },
      isAnimating(){
        return this.animating;
      },
      isForm(){
        return this.$el.classList.contains('form');
      }
    },
    methods: {
      flipOver(){
        this.changeSide('flip-left');
      },
      flipBack(){
        this.changeSide('flip-right');
      },
      flipLeft(){
        this.changeSide('left');
      },
      flipRight(){
        this.changeSide('right');
      },
      flipUp(){
        this.changeSide('up');
      },
      flipDown(){
        this.changeSide('down');
      },
      countSides(){
        this.sides   = this.$el.querySelectorAll('.side');

        this.sidesEl = this.$el.querySelector('.sides');

        if(! this.sidesEl){
          console.error('Sides Element not found !');
          return;
        }

        if(! this.sides.length ){
          console.error('Please add sides to use it !');
          return;
        }

        if(this.start && this.sides.length > this.start){
          this.index = this.start;
        }else{
          console.warn('value prop start is greater than actual sides. using 0 instead.')
        }

        this.addClass(this.sides[this.index], ['active']);

        if( this.isForm ){
          this.setSidesDim();
        }

        setTimeout(this.setShapeDim, 2000);
      },
      setSidesDim(){
        this.sides.forEach(row => {

          let form = row.querySelector('.form');

          let el = form.querySelector('input');
          
          let h = el.style.height ? el.style.height : 0;

          let w = el.style.height ? el.style.width : 0;

          el.style.minHeight = h;

          el.style.minWidth = w;

          this.sidesDim.push({h: ~~form.style.height.replace('px',''), w: ~~form.style.width.replace('px','')});
        });
      },
      changeSide(dir){
        if(this.animating ) return;

        this.animating = true;

        if( dir.includes('flip-') ){
          this.flipMode = true;

          dir = dir.replace('flip-','');
        }else{
          this.flipMode = false;
        }

        this.curDir = dir;

        this.prevIndex = this.index;

        let pos = this.index;

        pos += ( ~~this.nextDirs.includes(dir) || -1 );

        this.index = ( pos < 0 ) ? this.totalSides - 1 : pos % this.totalSides;

        this.setActiveSide();
      },
      setActiveSide(){
        this.setShapeDim();

        this.setDimensions();

        this.hidePrevSide();

        this.showCurSide();

        this.$el.classList.add('animating');

        this.setAnimationOnShapes();
      },
      setDimensions(){
        this.$el.style.height = this.shapeDim.h + 'px';
        this.$el.style.width = this.shapeDim.w + 'px';
      },
      setAnimationOnShapes(){
        let props = null;

        if( this.flipMode ){
          switch(this.curDir){
            case 'left':
              props = ("translateX(0px) rotateY(180deg)");
              break;

            case 'right':
              props = ("translateX(0px) rotateY(-180deg)");
              break;
          }          
        }else{
          switch (this.curDir){
            case 'right':
              props = ("translateX(0) translateZ(-"+this.wHalf+"px) rotateY(-90deg)");
              break;

            case 'left':
              props =  ("translateX(0) translateZ(-"+this.wHalf+"px) rotateY(90deg)");
              break;

            case 'down':
              props = ("translateY(0) translateZ(-"+this.hHalf+"px) rotateX(90deg)");
              break;

            case 'up': 
              props = ("translateY(0) translateZ(-"+this.hHalf+"px) rotateX(-90deg)");
              break;
          }
        }

        this.sidesEl.style.transform = props;
      },
      hidePrevSide(){
        let prevSide = this.sides[this.prevIndex];

        this.addClass(prevSide, ['hidden']);

        let props = null;

        if(this.flipMode){
          switch(this.curDir){
            case 'right':
            case 'left':
              props = ("rotateY(0deg)");
              break;
          }
        }else{
          switch(this.curDir){
            case 'right':
            case 'left':
              props = ("rotateY(0deg) translateZ("+this.wHalf+"px)");
              break;

            case 'up':
            case 'down':
              props = ("rotateY(0deg) translateZ("+this.hHalf+"px)");
              break;
          }
        }

        prevSide.style.transform = props;
      },
      showCurSide(){
        let curSide = this.sides[this.index];

        this.addClass(curSide, ['animating']);

        let styles = {};

        if( this.flipMode ){
           switch(this.curDir){
            case 'right':
            case 'left':
              styles = {left: '0px', transform: ("rotateY(-180deg)")};
              break;
          }
        }else{
          switch(this.curDir){
            case 'right':
              styles = {left: '0px', transform: ("rotateY(90deg) translateZ("+this.wHalf+"px)")};
              break;

            case 'left':
              styles = {left: '0px', transform: ("rotateY(-90deg) translateZ("+this.wHalf+"px)")};
              break;

            case 'up':
              styles = {top: '0px', transform: ("rotateX(90deg) translateZ("+this.hHalf+"px)")};
              break;

            case 'down':
               styles = {top: '0px', transform: ("rotateX(-90deg) translateZ("+this.hHalf+"px)")};
              break;
          }
        }   

        for (let s in styles){
          if (styles.hasOwnProperty(s)) {
            curSide.style[s] = styles[s];
          }
        }

        this.removeAnimation();
      },
      removeAnimation(){
        setTimeout(() =>{
          let curSide = this.sides[this.index], prevSide = this.sides[this.prevIndex];
          
          prevSide.classList.remove('active', 'hidden');

          this.addClass(curSide, ['active']);

          this.$el.removeAttribute('style');

          this.sidesEl.removeAttribute('style');

          prevSide.removeAttribute('style');

          curSide.removeAttribute('style');

          this.removeClass(this.$el, ['animating']);

          this.removeClass(curSide, ['animating']);

          this.animating = false;
        }, 1000);
      },
      addClass(elm, classList){
        elm.classList.add(classList.join(','));
      },
      removeClass(elm, classList){
        elm.classList.remove(classList.join(','));
      },
      setShapeDim(){
        this.shapeDim = {
          h: this.isForm ? this.sidesDim[this.index].h : this.$el.scrollHeight,
          w: this.isForm ? this.sidesDim[this.index].w : this.$el.scrollWidth
        };

        this.hHalf = this.shapeDim.h/2;
        this.wHalf = this.shapeDim.w/2;
      },
    },
    mounted(){
      this.countSides();
    }
  }
</script>