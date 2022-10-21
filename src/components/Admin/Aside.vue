<template>
    
    <nav class="naav">
      <div class="d-flex flex-column flex-shrink-0 p-3 text-white bg-dark" style="height: 100vh">
        <a  class="d-flex align-items-center mb-3 mb-md-0 me-md-auto text-white text-decoration-none">

          <span id="tit" class="fs-4"><img href="/" src="/src/assets/img/logo3.png" id="logo"/>GYM</span>
        </a>

        <hr />
        <br />
        <div id="wrap">
          <ul class=" nav nav-pills flex-column mb-auto">
            <li class="nav-item" id="li">
              <a class="nav-link  text-white">
                <img src="/src/assets/img/home.png" id="home" />
                <span class="tab-text">
                  <router-link class="link" to="/Admin/Home">Home</router-link>
                </span>
              </a>
            </li>
            <li id="li">
              <a class="nav-link text-white">
                <img src="/src/assets/img/boy.png" id="home" />
                <span class="tab-text">
                  <router-link class="link" to="/Admin/Clients">Clients</router-link>
                </span>
              </a>
            </li>
            <li id="li">
              <a class="nav-link text-white"><img src="/src/assets/img/asite.png" id="home" />
                <span class="tab-text">
                  <router-link class="link" to="/Admin/Assists">Assists</router-link>
                </span>
              </a>
            </li>
            <li id="li">
              <a class="nav-link text-white"><span class="fa fa-briefcase"></span>
                <span class="tab-text">
                  <router-link class="link" to="/Admin/Sales">Sales</router-link>
                </span>
              </a>
            </li>
            <li id="li">
              <a class="nav-link text-white"><span class="fa fa-bookmark"></span>
                <span class="tab-text">
                  <router-link class="link" to="/Admin/Inventory">inventori</router-link>
                </span>
              </a>
            </li>
          </ul>
        </div>
      </div>


       


    </nav>

</template>

<style scoped>
@import "../../assets/css/aside.css";
</style>