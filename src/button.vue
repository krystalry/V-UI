<template>
    <!--方法1：-->
    <!--<button class="g-button" v-if="iconPosition === 'right'">-->
        <!--<slot></slot>-->
        <!--<svg v-if="icon" class="icon">-->
            <!--<use :xlink:href=`#i-${icon}`></use>-->
        <!--</svg>-->
    <!--</button>-->
    <!--<button class="g-button" v-else>-->
        <!--<svg v-if="icon" class="icon">-->
            <!--<use :xlink:href=`#i-${icon}`></use>-->
        <!--</svg>-->
        <!--<slot></slot>-->
    <!--</button>-->
    <!--方法2：-->
    <button class="g-button" :class="{[`icon-${iconPosition}`]:true}">
        <slot></slot>
        <svg v-if="icon" class="icon">
            <use :xlink:href=`#i-${icon}`></use>
        </svg>
    </button>
</template>

<script>
    export default{
//        写法1
//        props: [`icon`,`iconPosition`]
//        写法2
        props: {
            icon: {},
            iconPosition: {
                type:String,
                default: 'left',
                validator(value) {
                    return value ==='left' || value ==='right'
                }
            }
        }
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