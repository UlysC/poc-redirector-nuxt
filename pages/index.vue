<template>
  <div id="app" style="text-align:center;">
    <img src="https://flevix.com/wp-content/uploads/2019/07/Ring-Loading-1.gif" alt="redirecting">
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  props: {
    msg: String
  },
  created(){
    if(process.browser){
      // let a = document.createElement('a')
      // a.href = window.location.
      console.log(window.location)
      const instance = window.location.host.split('.dev')[0]
      let from = window.location.pathname.substring(1)
      const url = '/.netlify/functions/map'
      axios.get(`${url}?from=${from}&instance=${instance}`)
      .then(res => {
        res;
        window.location.href = res.data
      })
      .catch(err => console.error(err))
    }
  },
  head(){
    return {
      title: '',
      meta: [
         {
            hid: 'prerender-status-code',
            name: 'prerender-status-code',
            content: '301',
          },
      ]
    }
  }
}
</script>

