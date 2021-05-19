<template>
    <header class="tvHeader" v-bind:class="{ tvHeader__detail: ['detail'].includes($route.name)}">
        <div class="tvContainer tvContainer--limit">
            <div class="tvHeader__box">
                <div class="tvHeader__box__left">
                    <div class="tvHeader__back">
                        <div class="tvHeader__back__arrow">
                            <a href="/">back</a>
                        </div>
                    </div>
                    <div class="tvHeader__logo">
                        <h1>shows</h1>
                    </div>
                </div>
                <div class="tvHeader__box__right">
                    <div class="tvHeader__settings">
                        <img src="@/assets/img/engranaje.svg" alt="">
                    </div>
                    <div class="tvHeader__search">
                        <img src="@/assets/img/lupa.svg" alt="">
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>
<script>
export default {
    name: "Header"
}
</script>