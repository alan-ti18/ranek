<template>
  <div class="loading">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
  </div>
</template>

<script>
export default {
  name: "PaginaCarregando",
}
</script>

<style scoped>
.loading {
  text-align: center;
  margin-top: 80px;
}

.loading span {
  display: inline-block;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #87f;
  margin: 4px;
  animation: dots .6s cubic-bezier(.6, .1, 1, .4) infinite alternate;
}

.loading span:nth-child(1) {
  animation-delay: .1s;

}

.loading span:nth-child(2) {
  animation-delay: .2s;

}

.loading span:nth-child(3) {
  animation-delay: .3s;

}

.loading span:nth-child(4) {
  animation-delay: .4s;

}

@keyframes dots {
  from {
    /* transform: translate3d(0, 0, 0); */
    transform: scale(.8);
  }

  to {
    /* transform: translate3d(0, 30px, 0); */
    transform: scale(1.2);
  }
}
</style>