<template>
    <AppLayout title="Chat">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                <ChatRoomSelection
                    v-if="currentRoom.id"
                    :rooms="chatRooms"
                    :current="currentRoom"
                    v-on:roomchanged="setRoom($event)"
                />
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <MessageContainer :messages="messages"/>
                    <InputMessage :room="currentRoom" v-on:messagesent="getMessages"/>
                </div>
            </div>
        </div>
    </AppLayout>
</template>

<script>
import AppLayout from '@/Layouts/AppLayout.vue';
import MessageContainer from "./MessageContainer.vue";
import InputMessage from "./InputMessage.vue";
import ChatRoomSelection from "./ChatRoomSelection.vue";
export default {
    components:{
        ChatRoomSelection,
        AppLayout,
        MessageContainer,
        InputMessage
    },
    data(){
        return{
            chatRooms:[],
            currentRoom:[],
            messages:[]
        }
    },
    methods:{
        getRooms(){
            axios.get('/chat/rooms')
                .then(res=>{
                    this.chatRooms = res.data;
                    this.setRoom(res.data[0])
                })
                .catch(err=>{
                    console.log(err)
                })
        },
        setRoom(room){
            this.currentRoom = room;
            this.getMessages();
        },
        getMessages(){
            axios.get(`/chat/room/${this.currentRoom.id}/messages`)
                .then(res=>{
                    this.messages = res.data
                })
                .catch(err=>{
                    console.log(err)
                })
        }
    },
    created() {
        this.getRooms();
    }
}
</script>
