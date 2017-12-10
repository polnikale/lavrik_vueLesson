<template>
  <div class="alert">
    <h3>{{x}} + {{y}} = ?</h3>
    <hr>
    <div class="buttons">
      <div class="btn btn-success" 
          v-for="number in answers"
          @click="onAnswer(number)">
       {{ number }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      x: mtRand(100,200), 
      y: mtRand(100,200)
    }
  },
  computed: {
    answers() {
      let good = this.x + this.y
      var res = [good];
      while (res.length < 4) {
        let num = mtRand(good -20, good +20);
        if (res.indexOf(num) === -1) {  
          res.push(num);
        }
      }
      return res.sort(() => {
        return Math.random() > 0.5;
      });
    }
  }
}

function mtRand(min, max) {
  let diff = max-min;
  return Math.floor(Math.random()*(diff+1) +min);
}
</script>

<style scoped>

.alert {
  padding-top: 20px;
  background-color: #eee;
}
.buttons {
  display: flex;
  justify-content: space-around;
}

</style>
