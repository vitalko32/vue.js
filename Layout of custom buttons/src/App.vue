<template>
    <div>
        <ButtonSB>
            <template #sell>1,234.00</template>
            <template #buy>1,234.00</template>
        </ButtonSB>
    </div>
</template>

<script>
import ButtonSB from "./components/Button.vue"

export default {
    name: "App",
    components: { ButtonSB },
}
</script>

<style>
</style>