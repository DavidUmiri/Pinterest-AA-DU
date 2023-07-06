<template>
    <div class="d-flex align-items-center justify-content-between">
        <div class="d-flex items-center">
            <button class="rounded-circle btn p-3 d-flex justify-content-center align-items-center">
                <img src="logo.png" alt="" style="width: 50px; height: 50px;">
            </button>
            <button v-for="(item,clave) in tabItems" :key="clave" @click="selectedTab= item.key" :class="`${selectedTab==item.key ? 'bg-dark text-white':'text-dark'} btn rounded-pill py-2 px-5 fw-bold`">
                {{ item.name }}
            </button>
        </div>
        <!-- <div class="">
            <i class="bi bi-search"></i>
            <input type="text" name="" id="" class="rounded-pill bg-light p-3" placeholder="search">
        </div> -->
        <div class="form-floating flex-grow-1 m-5">
          <input
            type="text"
            class="form-control rounded-pill"
            id="floatingInput"
            placeholder="usuario1"
          />
          <label for="floatingInput"><i class="bi bi-search"></i>  Username</label>
        </div>
</div>
</template>

<script setup>
import { ref } from 'vue';
const tabItems=[
    {name:'Home',key:'home'},
    {name:'Today',key:'today'}
    ]
let selectedTab = ref('home');
</script>

<style scoped>
/* img{
    width: 200px;
    height: 200px;
} */
.btn:hover{
    background-color: rgb(172, 172, 172);
}
</style>