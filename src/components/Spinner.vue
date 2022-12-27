<template>
  <div class="spin"></div>
</template>

<script>
export default {

}
</script>

<style>
.spin {
    border: 3px solid transparent;
    border-top-color: #ff8800;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    margin: 30px auto 0;
    animation: spin 1s ease infinite;
}
@keyframes spin {
    to {transform: rotateZ(360deg);}
}
</style>