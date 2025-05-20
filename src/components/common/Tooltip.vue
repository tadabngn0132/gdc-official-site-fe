<template>
    <div class="tooltip">
        <span class="tooltip__triangle"></span>
        <span class="tooltip__content">
            {{ content }}
        </span>
    </div>
</template>

<script>
export default {
    name: "Tooltip",
    props: {
        content: {
            type: String
        }
    }
}
</script>

<style scoped lang="scss">
$primary-background-color: #fff;
$secondary-background-color: #000;
$item-primary-color: #000;
$item-secondary-primary-color: #fff;
$item-secondary-color: #cb56b2;
$shadow-color: rgba(0, 0, 0, 0.25);

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.tooltip {
    display: flex;
    flex-direction: column;
    align-items: center;
    color: $item-secondary-primary-color;

    &__triangle {
        width: 0;
        height: 0;
        border-left: 0.4em solid transparent;
        border-right: 0.4em solid transparent;
        border-bottom: 0.5em solid $item-secondary-color;
    }
    
    &__content {
        font-family: Rubik, sans-serif;
        background-color: $item-secondary-color;
        padding: 0.75em 1em;
        box-shadow: 0 4px 12px $shadow-color;
        border-radius: 1em;
    }
}
</style>