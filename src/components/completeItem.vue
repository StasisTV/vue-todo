<template>
    <div id="item" v-on:mouseover="hover = true" v-on:mouseleave="hover = false">
        <div class="listItem">
            <p id="remove" v-bind:class="{'hidden': !hover}" v-on:click="remove">X</p>
            <p><s>{{ tag }}</s></p>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                isFav: false,
                hover: false    
            };
        },
        props: {
            tag: String,
        },
        methods: {
            remove() {
                this.$emit("remove", this.tag);
            }
        }
    }
</script>

<style lang="scss">
    #item {
        position: relative;
        cursor: pointer;
        font-weight: bold;
        width: fit-content;
        min-width: 10vw;
        margin: auto;
    }

    #remove {
        z-index: 2;
        position: absolute;
        left: calc(-10% - 0.15rem);
        width: 15%;
        color:rgb(165, 19, 19);

        transition-duration: 100ms;
    }

    .listItem {
        border-radius: 1vw;
        border-color: #3a3838;
        border-width: 0.235vw;
        border-style: solid;

        text-align: center;
        padding: 0.25vh;
        width: fit-content;
        max-width: 22vw;
        min-width: 10vw ;
        margin: 0.2vh;
        padding: 0.2vh;
    }

    p {
        padding: 0;
        margin: 0;
        max-width: 22vw;
        word-break: break-all;
    }

    .hidden {
        opacity: 0%;
    }
</style>