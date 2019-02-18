<template>
    <!--方法一：-->
    <button class="g-button" v-if="!iconPosition || iconPosition === 'left'">
        <svg v-if="icon" class="icon">
            <use :xlink:href=`#i-${icon}`></use>
        </svg>
        <slot></slot>
    </button>
    <button class="g-button" v-else>
        <slot></slot>
        <svg v-if="icon" class="icon">
            <use :xlink:href=`#i-${icon}`></use>
        </svg>
    </button>
</template>

<script>
    export default{
        props: [`icon`,`iconPosition`]
    }
</script>

<style lang="scss">
    .g-button {
        font-size: var(--font-size);
        height: var(--button-height);
        padding: 0 1em;
        border-radius: var(--button-radius);
        border-color: var(--button-color);
        background: var(--button-bg);
    }

    .g-button:hover {
        border-color: var(--button-color-hower);
    }

    .g-button:active {
        background-color: var(--button-active-bg);
    }

    .g-button:focus {
        outline: none;
    }
</style>