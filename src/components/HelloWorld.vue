<template>
  <div class="hello">

    <h1>{{ msg }} at - " <input class="inputTest" type="text" v-model="actualProgress" /> % "</h1>

    <!-- <h3> works best at 1920*1080 screen resolution </h3> -->
    
    <div class="box" >

      <div class="progress-bar part2">

        <div class="end-part" :style="{transform: 'rotate(290deg)'}">
          <div 
            v-for="(i, index)  in progress.slice(0, 80)" 
            :key="i" 
            :id="`progress-${index}`" 
            :class="`progress-${i}`"
            :style="{
              transform: 'rotate(180deg)',
              marginTop: '0'
            }"
            class="outer "
          > 
            <div :style="{background: (actualProgress * 10 - 10) >= i ? 'gold' : 'transparent'}" class="inner"></div>
          </div>
        </div>

        <div 
          v-for="(i, index)  in progress.slice(80, 1000)" 
          :key="i" 
          :class="(i >= 80 && i <= 150) ? 'arc-piece' : 'arc-not'"
          :style="{
            transform: (i >= 80 && i <= 150) ? `rotate(${(index - 120) + 50}deg)` : '',
            marginLeft: i === 151 ? '170.1px': '',
            marginTop: (i >=150 && i <= 1000)? '0.3px' : ''
          }"
        >
          <div 
            :id="`progress-${index}`" 
            :class=" (i >= 80 && i <= 150) ? `arc-piece-outer progress-${i}` : `progress-${i}`"
            class="outer "
            
          > 
            <div :style="{background: (actualProgress * 10 - 10) >= i ? 'gold' : 'transparent'}" class="inner"></div>
          </div>
        </div>

      </div>

     </div>
   
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  data () {
    return {
      progress: [...Array(1000).keys()],
      actualProgress: 56,
    }
  },

  mounted () {  
    console.log(this.progress.slice(150, 225)[0])
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  .inputTest{
    font-size: 30px;
    background-color: transparent;
    width: 50px;
    color: white;
  }

  .box {
    width: 1000px;
    height: 100px;
    border: 1px solid black;
    display: flex;
    padding: 0 0 0 0;
    justify-content: center;
  }

  .progress-0 {
    padding: 0 10px 0 0;
    border-top-right-radius:10px;
    border-bottom-right-radius: 10px
  }

  .progress-0 > .inner {
    padding: 0 10px 0 0;
    border-top-right-radius:10px;
    border-bottom-right-radius: 10px
  }

  .progress-999 {
    padding: 0 10px 0 0;
    border-top-right-radius:10px;
    border-bottom-right-radius: 10px
  }

  .progress-999 > .inner {
    padding: 0 10px 0 0;
    border-top-right-radius:10px;
    border-bottom-right-radius: 10px
  }

  .outer {
    background-color: grey;
    height: 15px;
    width:0.2px;
    display: flex;
    justify-content: center;
  }

  .inner {
    height: 4px;
    width: 100%;
    margin: auto 0 auto 0;
  }

  .hello {
    /* height: 100vh; */
    background: rgb(44, 43, 43);
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .end-part {
    display:flex;
    align-items: flex-start;
    position: absolute;
    margin: 55px 73px 0 0;
  }

  /* ------------------------ progress bar arc -------------------------- */

  .progress-bar {
    --r: 50px;
    /* radius of the circle */
    --t: 8;
    /* total number of books */
    position: relative;
    display: flex;
    justify-content: center;
    --w: calc(var(--r) * 1.2);
    /* the top of the book is 20% out further than the edge of the circle */
    width: calc(2 * var(--w));
    height: calc(1.662 * var(--w));
    margin: 0;
    padding: 0 0 0 0;
    transform: rotate(0);
    margin: 0 0 0 0;
  }

  .progress-bar::before {
    content: '';
    width: calc(2 * var(--r));
    border: 1px solid transparent;
    aspect-ratio: 1 / 1;
    border-radius: 0;
    position: absolute;
    top: calc(var(--r) * 0.1);
    left: calc(var(--r) * 0.2);
    display: inline-block;
    margin: 0;
    padding: 0;
  }

  .arc-piece {
    height: calc(var(--r)/1.5 * 1.2);
    width: calc(var(--r)/1.5 / 5);
    position: absolute;
    bottom: var(--w);
    left: calc(var(--w) - (0.5 * var(--r) / 5));
    transform-origin: center bottom;
    position: absolute;
    margin: 0;
    padding: 0;
  }

  .arc-piece-outer {
    height: calc(var(--r)/4 * 1.2);
    width: calc(var(--r)/4 / 5);
  }



</style>
