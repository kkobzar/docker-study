<template>
    <div class="grid grid-cols-2">
        <div class="font-bold text-xl">
            {{selected.name}} Chat
        </div>
        <div>
            <select v-model="selected"
                    @change="$emit('roomchanged', selected)" class="float-right">
                <option v-for="(r, index) in rooms" :key="index" :value="r">
                    {{r.name}}
                </option>
            </select>
        </div>
    </div>
</template>

<script>
export default {
    name: "ChatRoomSelection",
    props: ['rooms','current'],
    data(){
        return {
            selected:''
        }
    },
    created() {
        this.selected = this.current;
    }
}
</script>

<style scoped>

</style>
