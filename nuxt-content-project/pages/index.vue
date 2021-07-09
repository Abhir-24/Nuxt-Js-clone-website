<template>
  <div class="container">
      <Navbar />

  <div class="container-items">

    <div class="sidebar">

      <Sidebar />

    </div>
    <div class="main-part">

      <h1>{{page.title}}</h1>
      <p><nuxt-content :document="page" /></p>

      <div class="bottom-part"></div>

    
    </div>



  </div>
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue'
import Sidebar from '../components/SIdebar.vue';
export default {
  components: {
    Navbar,
    Sidebar
  },

    async asyncData ({ $content }) {
    const page = await $content('displaying').fetch()

    return {
      page
    }
  }
}
</script>

<style>
*
{
  margin: 0;
  padding: 0;
  box-sizing: border-box;  
}

.container
{
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
  justify-content: center;
  align-items: center;
  

}
.navbar-container
{
  width: 100%;
  
}


.container-items 
{
  
  height: 100vh;
  width: 80%;
  display: flex;

  

}
.sidebar 
{
  height: 80vh;
  

  flex: 0.7;
  
  

}
.main-part
{
  flex: 2;
  padding: 30px;
  
}

h1
{
  
  color: #2f495ecb;
  margin-bottom: 20px;

}

svg
{
  height: 60%;
  width: auto;
  padding-right: 20px;
  padding-top: -60px;
  margin-top: -14px;
  color: rgba(0, 0, 0, 0.541);
}

</style>