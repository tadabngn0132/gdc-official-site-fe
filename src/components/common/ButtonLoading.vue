<template>
    <div class="button-loading">
        <span class="button-loading__loader"></span>
    </div>
</template>

<script>
export default {
    name: "ButtonLoading",
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

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.button-loading {
    display: flex;
    justify-content: center;
    align-items: center;

    &__loader {
        width: 24px;
        height: 24px;
        border: 0.195em solid $item-secondary-primary-color;
        border-bottom-color: $item-secondary-color;
        border-radius: 50%;
        display: inline-block;
        box-sizing: border-box;
        animation: rotation 1s linear infinite;
    }

    @keyframes rotation {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
    } 
}
</style>