<template>
    <div class="tooltip">
        <span class="tooltip__triangle up"></span>
        <span class="tooltip__triangle down"></span>
        <span class="tooltip__triangle left"></span>
        <span class="tooltip__triangle right"></span>
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
        },
        trianglePositionWithContent: {
            type: String
        }
    },
    data() {
        return {
            trianglePosition: ''
        }
    },
    methods: {
        setTrianglePosition() {
            const tooltipContainer = this.$el
            const upTriangle = this.$el.querySelector('.tooltip__triangle.up')
            const downTriangle = this.$el.querySelector('.tooltip__triangle.down')
            const leftTriangle = this.$el.querySelector('.tooltip__triangle.left')
            const rightTriangle = this.$el.querySelector('.tooltip__triangle.right')

            upTriangle.style.display = 'none';
            downTriangle.style.display = 'none';
            leftTriangle.style.display = 'none';
            rightTriangle.style.display = 'none';

            if (this.trianglePositionWithContent === 'up') {
                tooltipContainer.style.flexDirection = 'column'
                upTriangle.style.display = 'block'
            } else if (this.trianglePositionWithContent === 'down') {
                tooltipContainer.style.flexDirection = 'column-reverse'
                downTriangle.style.display = 'block'
            } else if (this.trianglePositionWithContent === 'left') {
                tooltipContainer.style.flexDirection = 'row'
                leftTriangle.style.display = 'block'
            } else {
                tooltipContainer.style.flexDirection = 'row-reverse'
                rightTriangle.style.display = 'block'
            }
        }
    },
    mounted() {
        this.setTrianglePosition()
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
    position: relative;

    &__triangle {
        width: 0;
        height: 0;
        position: absolute;
        z-index: 2;
        
        &.up {
            bottom: 93%;
            display: none;
            border-left: 0.4em solid transparent;
            border-right: 0.4em solid transparent;
            border-bottom: 0.5em solid $item-secondary-color;
        }
        
        &.down {
            top: 93%;
            display: none;
            border-left: 0.4em solid transparent;
            border-right: 0.4em solid transparent;
            border-top: 0.5em solid $item-secondary-color;
        }

        &.left {
            right: 93%;
            display: none;
            border-bottom: 0.4em solid transparent;
            border-top: 0.4em solid transparent;
            border-right: 0.5em solid $item-secondary-color;
        }

        &.right {
            left: 93%;
            display: none;
            border-bottom: 0.4em solid transparent;
            border-top: 0.4em solid transparent;
            border-left: 0.5em solid $item-secondary-color;
        }
    }

    
    &__content {
        font-family: Rubik, sans-serif;
        outline: none;
        background-color: $item-secondary-color;
        padding: 0.5em 0.75em;
        font-size: 13px;
        border-radius: 1em;
        border: unset;
    }
}
</style>