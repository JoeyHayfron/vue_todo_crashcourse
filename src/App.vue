<template>
  <div id="nav">
    <Header />

  </div>
  <router-view/>
</template>

<script>
import Header from './components/layouts/Header';

export default {
  name: 'app',
  components: {
    Header,
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
    margin:0;
    padding: 0;
  }

  body{
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
</style>
