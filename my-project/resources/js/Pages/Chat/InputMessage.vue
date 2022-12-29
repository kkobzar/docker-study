<template>
    <div class="relative h-10 m-1">
        <div class="grid grid-cols-6 border-solid border-2 border-sky-500">
            <text-input type="text" v-model="message"
            @keyup.enter="mendMessage()"
            placeholder="Enter message"
            class="col-span-5 outline-none p-1"/>
            <button @click="sendMessage()"
            class="place-self-end bg-gray-500 hover:bg-blue-700 p-1 mt-1 rounded text-white">
                Send
            </button>
        </div>
    </div>
</template>

<script>
import TextInput from "../../Components/TextInput.vue";
export default {
    name: "InputMessage",
    components: {TextInput},
    props:['room'],
    data(){
        return{
            message: ''
        }
    },
    methods:{
        sendMessage(){
            if(!this.message)return;
            axios.post(`/chat/room/${this.room.id}/message`,{
                message: this.message
            })
                .then(res=>{
                    if (res.status == 201){
                        this.message= '';
                        this.$emit('messagesent');
                    }
                })
                .catch(err=>console.log(err))
        }
    }
}
</script>

<style scoped>

</style>
