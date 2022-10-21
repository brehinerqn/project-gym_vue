<style scoped>
@import "../assets/css/style.css";
</style>
<template>
    <header>
        <a href="#" class="logo"><span>Fit</span>Ness</a>
        <div class="toggle"><img src="../assets/image/toggle.png"></div>
    </header>
    <div class="banner">
        <video src="../assets/image/bg.mp4" autoplay muted loop type="mp4"></video>
        <div class="texBox">
            <h2>More Than Fitness</h2>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit.
                Aliquid, nisi. Libero dolorem qui repudiandae voluptatum aperiam hic tempore,</p>
            <router-link to="/login">
                <a href="#">Login</a>
            </router-link>
            <br>
            <br>
            <router-link to="/register">
                <a href="#">Register</a>
            </router-link>
        </div>
        <div class="ImgBox">
            <img src="../assets/image/man.png">
        </div>
        <ul class="sci">
            <li> <a href="#"><img src="../assets/image/facebook.png"></a></li>
            <li> <a href="#"><img src="../assets/image/instagram.png"></a></li>
            <li> <a href="#"><img src="../assets/image/twitter.png"></a></li>
        </ul>
    </div>
</template>