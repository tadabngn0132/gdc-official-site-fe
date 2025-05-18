<template>
    <div class="not-found">
        <span class="not-found__title">404</span>
        <span class="not-found__sub-title">Page Not Found</span>
        <span class="not-found__details">Sorry, but the page you are looking for is not found.</span>
        <span class="not-found__details">Don't worry, go back to the home page to continue experiencing our website.</span>
        <router-link to="/" class="not-found__button">Go Back Home Page</router-link>
    </div>
</template>

<script>
export default {
    name: "NotFound"
}
</script>

<style scoped lang="scss">
$primary-background-color: #fff;
$secondary-background-color: #000;
$item-primary-color: #000;
$item-secondary-primary-color: #fff;
$item-secondary-color: #cb56b2;

.not-found {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: $item-primary-color;

    &__title {
        font-family: Poppins, sans-serif;
        font-size: 6.75em;
        font-weight: 500;
        
    }

    &__sub-title {
        font-size: 1.5em;
        font-weight: 500;
        margin-bottom: 1em;
    }

    &__details {
        margin-bottom: 0.5em;
        font-weight: 450;
    }

    &__button {
        display: inline-block;
        background-color: $secondary-background-color;
        color: $item-secondary-primary-color;
        padding: 0.75rem 1.5rem;
        border-radius: 1em;
        text-decoration: none;
        margin-top: 1.5em;
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