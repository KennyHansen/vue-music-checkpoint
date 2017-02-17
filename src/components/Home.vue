<template>
  <div class="home">
    <!-- YOU WILL PROBABLY END UP WITH SOMETHING LIKE THIS -->
    <my-tunes class="my-tunes"></my-tunes>
    <itunes class="itunes"></itunes>
  </div>
</template>

<script>
import Itunes from './Itunes'
import MyTunes from './MyTunes'
export default {
  name: 'home',
  components: {
    Itunes,
    MyTunes
  },
  data () {
    return {
      
    }
  }
}
</script>


<style>
/**
* YOU SHOULD PROBABLY MAKE THIS LOOK BETTER :)
* BOOTSTRAP IS FOR THE WEAK FLEXBOX IS KING
* -- McCall
**/
.my-tunes{
  display: inline-block;
  min-height: 500px;
  min-width: 50%;
  background: palegreen;
}

.itunes{
  display: inline-block;
  background: darkslategray;
  min-height: 500px;
  min-width: 45%;
}

</style>
