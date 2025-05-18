<template>
    <div class="loading">
        <span class="loading__loader"></span>
    </div>
</template>

<script>
export default {
    name: "Loading",
    data() {
        return {
            // Add any data properties if needed
        };
    },
    methods: {
        // Add any methods if needed
    },
};
</script>

<style scoped lang="scss">
$item-primary-color: #000;
$item-secondary-primary-color: #fff;
$item-secondary-color: #cb56b2;

.loading {
    display: flex;
    justify-content: center;
    align-items: center;

    &__loader {
        width: 48px;
        height: 48px;
        border-radius: 50%;
        display: inline-block;
        position: relative;
        border: 3px solid;
        border-color: $item-secondary-color $item-secondary-color transparent transparent;
        box-sizing: border-box;
        animation: rotation 1s linear infinite;
    
        &::after,
        &::before {
            content: '';  
            box-sizing: border-box;
            position: absolute;
            left: 0;
            right: 0;
            top: 0;
            bottom: 0;
            margin: auto;
            border: 3px solid;
            border-color: transparent transparent $item-primary-color $item-primary-color;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            box-sizing: border-box;
            animation: rotationBack 0.5s linear infinite;
            transform-origin: center center;
        }
        &::before {
            width: 32px;
            height: 32px;
            border-color: $item-secondary-color $item-secondary-color transparent transparent;
            animation: rotation 1.5s linear infinite;
        }
            
        @keyframes rotation {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        } 
        @keyframes rotationBack {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(-360deg);
            }
        }
    }
}
</style>