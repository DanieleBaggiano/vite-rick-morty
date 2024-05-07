<script>
import { store } from "/src/store";
export default {
    data() {
        return {
            store,
        }
    },
}
</script>

<template>
    <select>
        <option v-for="item in store.cardsList" value="options">{{ item.status}}</option>
    </select>
</template>

<style scoped lang="scss">
    @use "../style/partials/variables" as *;
    @use "../style/partials/mixins" as *;
</style>