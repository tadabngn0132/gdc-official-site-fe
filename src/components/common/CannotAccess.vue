<template>
    <div class="cannot-access">
        <div class="cannot-access__content">
            <h1 class="cannot-access__title">Access Denied</h1>
            <p class="cannot-access__description">You do not have permission to access this page.</p>
            <router-link to="/" class="cannot-access__button">Go Back Home Page</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: "CannotAccess",
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
$primary-background-color: #fff;
$secondary-background-color: #000;
$item-primary-color: #000;
$item-secondary-primary-color: #fff;
$item-secondary-color: #cb56b2;

.cannot-access {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 75vh;
    background-color: $primary-background-color;

    &__content {
        text-align: center;
        padding: 3rem 6rem;
        border-radius: 1em;
        box-shadow: 0 6px 18px rgba(203, 86, 178, 0.25);

        @media screen and (max-width: 768px) {
            padding: 2rem 0.5rem;
            box-shadow: none;
        }
    }

    &__title {
        font-size: 3.05rem;
        color: $item-primary-color;
        margin: 0 0 1.5rem 0;

        @media screen and (max-width: 768px) {
            font-size: 2.75rem;
        }
    }

    &__description {
        font-size: 1.05rem;
        font-weight: 450;
        color: $item-primary-color;
        margin-bottom: 1.5rem;
    }

    .cannot-access__button {
        display: inline-block;
        background-color: $secondary-background-color;
        color: $item-secondary-primary-color;
        padding: 0.75rem 1.5rem;
        border-radius: 1em;
        text-decoration: none;
        font-size: 0.95rem;
        font-weight: 500;
        transition: all 0.3s ease;

        &:active {
            color: $item-primary-color;
            background-color: $item-secondary-color;
        }

        &:hover {
            color: $item-primary-color;
            background-color: $item-secondary-color;
            transform: translateY(-2px);

            @media screen and (max-width: 768px) {
                transform: translateY(0);
            }
        }
    }
}
</style>