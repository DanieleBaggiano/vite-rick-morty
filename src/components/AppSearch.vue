<script>
import { store } from "/src/store";
export default {
    data() {
        return {
            store,
            status: ["Alive", "Dead", "Unknown"]
        }
    },
}
</script>

<template>
    <select @change="$emit('filter')" v-model="store.selectedStatus">
        <option v-for="item in status" :value="item">{{ item }}</option>
    </select>
</template>

<style scoped lang="scss">
    @use "../style/partials/variables" as *;
    @use "../style/partials/mixins" as *;
</style>