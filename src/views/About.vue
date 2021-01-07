<template>
  <div class="about">
    <h2>This is an about page</h2>
  </div>
</template>

<script>

</script>

<style>
h2{
  color: #ff0000;
  position: relative;
  animation-name: example;
  animation-duration: 4s;
  animation-direction: reverse;
}
@keyframes example {
  0%   {color:red; left:0px; top:0px;}
  25%  {color:yellow; left:200px; top:0px;}
  50%  {color:blue; left:200px; top:200px;}
  75%  {color:green; left:0px; top:200px;}
  100% {color:red; left:0px; top:0px;}
}
</style>
