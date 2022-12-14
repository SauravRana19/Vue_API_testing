<template>
    <div class="fixed-header">
        <div class="container">
            <nav>
                <a href="#"> Home </a>
                <a href="#"> Events </a>
                <a href="#"> About Us</a>
                
            </nav>
        </div>
    </div>
</template>
<script>
export default {
    title: 'head-er'
}
</script>
<style>
body {
    padding-top: 60px;
    padding-bottom: 40px;
}

.fixed-header {
    width: 100%;
    position: fixed;
    background: #333;
    padding: 10px 0;
    color: #fff;
}

.fixed-header {
    top: 0;
}

.container {
    width: 80%;
    margin: 0 auto;
}

nav a {
    color: #fff;
    padding: 7px 25px;
   
}
</style>