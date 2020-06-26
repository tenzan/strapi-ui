<template>
  <div class="home">
    <HelloWorld/>
    <ul>
      <li v-for="location in locations" :key="location.code">
        <p>{{location.code}}  {{location.name_jp}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data() {
    return {
      locations: {
        code: '',
        name_jp: ''
      }
    }
  },
  created() {
    axios.get('http://128.199.169.59/locations')
    .then(response => (this.locations = response.data))
    .catch(error => {console.log(error)})
  }
}
</script>
