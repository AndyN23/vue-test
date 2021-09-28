<template>
    <button class="button">
        <slot></slot>
    </button>
</template>

<script>
    export default {
        name: 'my-button'
    }
</script>

<style lang="scss" scoped>

.button{
    padding: 20px 40px;
    border: 1px solid #09491f;
    border-radius: 4px;
    background-color: #128038;
    color: white;
    font-weight: 600;
    transition: all 0.3s ease;

    &:hover{
        background-color: #0f692f;
    }
}

</style>