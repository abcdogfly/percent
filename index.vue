<template>
<div class="line">
    <p :style="getWidth">
        <span class="precent-animate" :style="getColor"></span>
    </p>
</div>
</template>

<script>
export default {
  props: ["option"],
  computed: {
    // 设置宽
    getWidth() {
      const option = this.option
      const percent = option.num / option.total
      return `width: ${percent * 100}%;`
    },
    // 设置渐变
    getColor() {
      const option = this.option
      return `background: linear-gradient(-99deg,${option.colorStart} 0%,${option.colorEnd} 100%);`
    }
  }
}
</script>

<style lang="scss" scoped>
.line {
    position: relative;
    width: 100%;
    height: 0.2rem;
    background: rgba(45,61,88,0.4);
    border-radius: 0.1rem;
    p {
    position: absolute;
    left: 0;
    top: 0;
    height: 0.2rem;
    border-radius: 0.1rem;
    .precent-animate {
        position: absolute;
        left: 0;
        top: 0;
        bottom: 0;
        border-radius: 0.1rem;
        animation: process 1s linear forwards;
    }
    }
    @keyframes process
    {
    0%{
        left:0;
        right:100%;
    }
    20%{
        right:80%
    }
    40%{
        right:60%;
    }
    60%{
        right:40%;
    }
    80%{
        right:20%;
    }
    100%{
        right:0;
    }
    }
}
</style>