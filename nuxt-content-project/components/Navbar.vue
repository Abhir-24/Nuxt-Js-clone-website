<template>
<div class="navbar-container `${(window.scrolly > 300) ? 'activeborder' : ''}`">

    <div class="navbar-items">

        <div class="navbar-logo">
            <img src="https://warlord0blog.files.wordpress.com/2019/10/nuxtjs_logo.png" alt="logo">
        </div>
        <div class="nav-content">
            <ul>
                <li>
                    <a href="https://nuxtjs.org/docs/2.x/get-started/installation">DOCS</a>
                    <a href="https://nuxtjs.org/examples">EXAMPLE</a>
                    <a href="https://nuxtjs.org/resources">RESOURCES</a>
                    <a href="https://nuxtjs.org/blog">BLOG</a>
                    <a href="https://masteringnuxt.com/?utm_source=nuxt&utm_medium=link&utm_campaign=navbar_link">VIDEO COURSES</a>
                    
                </li>
            </ul>
        </div>

        <div class="navbar-searchbar">

            <form action="submit">
                <input id="input" type="text" placeholder="Search ('/' to focus)">
            </form>
        </div>

       <div class="wrapper">
    <nav>
      <input type="checkbox" id="show-menu">
      <label for="show-menu" class="menu-icon"><i class="fas fa-bars"></i></label>
      <div class="content">

        <ul class="links">

          <li>
            <a href="#" class="desktop-link">Getting Started</a>
            <input type="checkbox" id="show-features">
            <label for="show-features">Getting Started</label>
            <ul>
              <li><a href="#">Introduction</a></li>
              <li><a href="/writing">Writing Content</a></li>
              <li><a href="#">Fetching Content</a></li>
              <li><a href="/">Displaying Content</a></li>
              <li><a href="#">Configuration</a></li>
              <li><a href="#">Advanced</a></li>
            </ul>
          </li>

          <li>
            <a href="#" class="desktop-link">Examples</a>
            <input type="checkbox" id="show-services">
            <label for="show-services">Examples</label>
            <ul>
              <li><a href="#">Basic Usage</a></li>
              <li><a href="#">TailwindCSS Typography</a></li>
              <li><a href="#">Docs Theme</a></li>
            </ul>
          </li>

          <li>
            <a href="#" class="desktop-link">Themes</a>
            <input type="checkbox" id="show-services">
            <label for="show-services">Themes</label>
            <ul>
              <li><a href="#">Docs</a></li>
            </ul>
          </li>

          <li>
            <a href="#" class="desktop-link">Community</a>
            <input type="checkbox" id="show-services">
            <label for="show-services">Community</label>
            <ul>
              <li><a href="#">Snippets</a></li>
              <li><a href="#">Integrations</a></li>
              <li><a href="#">Releases</a></li>
            </ul>
          </li>
          
        </ul>
      </div>
      
    </nav>
  </div>




    </div>


</div>
    
</template>
<script>
export default {
    name: 'Navbar'
}
</script>
<style scoped>
*
{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    transition: 0.4s ease;
}
.navbar-container
{
    width: 100%;
    height: 130px;
    display: flex;
    justify-content: center;
    align-items: center;
   

}
.activeborder
{
     border-bottom: 1px solid rgba(0, 0, 0, 0.24);
}
.navbar-items 
{
    width: 80%;
    height: 150px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    
}
.navbar-logo
{    
    height: 80%;
    width: 250px;
    object-fit: contain;   
}

.navbar-logo img
{
    height: 100%;
    width: 250px;
    object-fit: contain;
}

.nav-content 
{
    height: 80%;
    width: 600px;

    display: flex;
    justify-content: center;
    align-items: center;
}
.nav-content ul

{
    list-style: none;

}
.nav-content ul li a 
{
    text-decoration: white;
    color: rgba(0, 0, 0, 0.747);
    font-size: 1.1rem;
    padding: 10px;


}
.nav-content ul li a:hover
{
    color: #35bb80;
}
.navbar-searchbar 
{
    height: 80%;
    width: 300px;
    display: flex;
    justify-content: center;
    align-items: center;
}
#input
{
    background-color: #d8d8e41f;
    border: none ;
    height: 40px;
    width: auto;
    border-radius: 20px;
    outline: none;
    

}
input[type = "text"]
{
    padding-left: 20px;
    font-size: 1.1rem;
}
::placeholder {
  color: rgba(2, 23, 24, 0.295);
  padding: 20px;
  font-size: 1.1rem; 
}

@media screen and (max-width : 1000px) {
    .nav-content {
        display: none;
    }

    .navbar-logo img {
        height: 80%;
        width: 180px;
    }
}

@media screen and (min-width : 800px) {
    .wrapper {
        display: none;
    }
    
}

@media screen and (max-width : 800px) {
    .navbar-searchbar {
        display: none;
    }
    
}


@media screen and (max-width: 1250px){
  .wrapper {
    z-index: 100;
  }

  .wrapper nav{
    max-width: 100%;
    padding: 0 20px;
  }
  nav .content .links{
    margin-left: 30px;
    list-style-type: none;
  }
  

  .content .links li a{
    padding: 8px 13px;
  }
}

@media screen and (max-width: 900px){
  .wrapper .menu-icon{
    display: block;
  }
  .wrapper #show-menu:checked ~ .menu-icon i::before{
    content: "\f00d";
  }
  nav .content .links{
    display: block;
    position: fixed;
    background: #F3F0D7;
    height: 100%;
    width: 100%;
    top: 70px;
    left: -100%;
    margin-left: 0;
    max-width: 350px;
    overflow-y: auto;
    padding-bottom: 100px;
    transition: all 0.3s ease;
  }

  .content .links li:hover > ul{
  top: 70px;
  opacity: 1;
  visibility: visible;
  transition: all 0.3s ease;
}

  nav #show-menu:checked ~ .content .links{
    left: 0%;
  }

  .content .links ul li a{
  display: block;
  width: 100%;
  line-height: 30px;
  text-decoration: none;
  
  border-radius: 0px!important;
}

  .content .links ul{
  position: absolute;
  background: #171c24;
  top: 80px;
  z-index: -1;
  opacity: 0;
  visibility: hidden;
}

  .content .links li{
    margin: 15px 20px;
    
  }

  .content .links li a,
  .content .links li label{
    line-height: 40px;
    font-size: 20px;
    display: block;
    padding: 8px 18px;
    cursor: pointer;
  }
  .content .links li a.desktop-link{
    display: none;
  }

  .content .links ul,
  .content .links ul ul{
    position: static;
    opacity: 1;
    visibility: visible;
    background: none;
    max-height: 0px;
    overflow: hidden;
    list-style-type: none;
  }

  .content .links ul li a {
    color: lightslategray;
  }

  .content .links ul li a:hover {
    background-color: #66DE93;
  }

  input[type="checkbox"] {
    opacity: 0;
  }

  #show-menu {
    opacity: 1;
  }


  .content .links #show-features:checked ~ ul,
  .content .links #show-services:checked ~ ul,
  .content .links #show-items:checked ~ ul{
    max-height: 100vh;
  }
  .content .links ul li{
    margin: 7px 20px;
  }
  .content .links ul li a{
    font-size: 18px;
    line-height: 30px;
    border-radius: 5px!important;
  }
}

@media screen and (max-width: 400px){
  .wrapper nav{
    padding: 0 10px;
  }
  .content .logo a{
    font-size: 27px;
  }

}


</style>