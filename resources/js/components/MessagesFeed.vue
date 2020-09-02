<template>
    <div class="feed" ref="feed">
        <ul v-if="contact">
            <li v-for="message in messages" :class="`message${message.to == contact.id ? ' sent' : ' received'}`" :key="message.id">
                <div class="text">
                    {{ message.text }}
                </div>
            </li>
        </ul>
    </div>
</template>


<script>
export default {

    props: {
        contact:{
            type:Object
        },
        messages: {
            type:Array,
            required:true
        }
    },
    methods:{
        scrollToBottom(){
            setTimeout(() => {
                // this.$refs.feed.scrollTop = this.$refs.feed.clientHeight - this.$refs.feed.clientHeight;
                this.$refs.feed;
                this.$refs.feed.scrollTop = this.$refs.feed.scrollHeight;
            }, 80);

        },

    },
    watch: {
        contact(contact) {
            this.scrollToBottom();
        },
        messages(messages) {
            this.scrollToBottom();
        }
    },




}



</script>






<style lang="scss" scoped>

.feed {
    //background: #adb5bd;
    height: 100%;
    max-height: 470px;
    overflow: scroll;

    ul {
        list-style-type: none;
        padding: 5px;

        li.message {
            margin: 10px 0;
            width: 100%;
            .text {
                max-width: 200px;
                border-radius: 20px;
                padding: 12px;
                display: inline-block;
            }
        }
        li.message.received {
            text-align: right;
            .text{
                background: #d8d8d882;
            }

        }

        li.message.sent {
            text-align: left;

            .text{
                background:#c8e6ff;
            }

        }
    }

}

</style>
