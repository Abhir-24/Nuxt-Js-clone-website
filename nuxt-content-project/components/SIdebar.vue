<template>
  <div class="sidebar-container">

    <div class="sidebar">
      <h5 class="side-header">Getting Started</h5>
      <a href="#">Introduction</a>
      <a href="/writing">Writing content</a>
      <a href="#">Fetching content</a>
      <a href="/">Displaying content</a>
      <a href="#">Configuration</a>
      <a href="#">Advanced</a>    
    </div>
    
    <div class="sidebar">
      <h5 class="side-header">Themes</h5>
      <a href="#">Docs</a>  
    </div>
    
    <div class="sidebar">
      <h5 class="side-header">Examples</h5>
      <a href="#">Basic Usage</a>
      <a href="#">TailwindCSS Typography</a>
      <a href="#">Docs Theme</a> 
    </div>
     
    <div class="sidebar">
      <h5 class="side-header">Community</h5>
      <a href="#">Snippets</a>
      <a href="#">Integrations</a>
      <a href="#">Releases</a>
    </div> 
    
  </div>
</template>
<script>
export default {
  
}
</script>
<style scoped>
*
{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  transition: all 0.4s ease;
}
.sidebar-container 
{
  height: 100%;
  width: 100%;
  background-color: white;
  display: flex;
  flex-direction: column;
  overflow-y: scroll ;
  display: flex;

}

.sidebar
{
  
  width: 100%;
  height: auto;
  margin-bottom: 20px;
  
}

.side-header
{
  padding: 10px;
  color: rgba(0, 0, 0, 0.568);
  font-size: 1.09rem;
  font-weight: 500;
  margin-bottom: 20px;
  
}

.sidebar 
{
  display: flex;
  justify-content: center;
  flex-direction: column;
  


}
.sidebar a
{
  padding-left:30px;
  padding-bottom: 10px;
  color: rgba(0, 0, 0, 0.63);
  font-size: 17px;
  text-decoration: rgba(0, 0, 0, 0.658);

}
.sidebar a:hover
{
  color: #35bb80;
}
.active

{
  color: green;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 128, 0, 0.466);
  display: flex;
  
  align-items: center;
}


@media screen and (max-width : 800px) {
  .sidebar-container {
    display: none;
  }
}

</style>
