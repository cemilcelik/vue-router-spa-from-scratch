<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12">
                <h1>Vue-Router-Spa</h1>
            </div>
            <div class="col-xs-12">
                <transition name="fade">
                    <router-view></router-view>
                </transition>
            </div>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style>
.fade-enter-active, .fade-leave-active{
    transition: opacity .5s;
}
.fade-enter, .fade-leave{
    opacity: 0;
}
</style>
