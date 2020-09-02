<template>
    <div class="contact-list">
        <ul>
            <li  v-for="(contact, index) in contacts" :key="contact.id" @click="selectContact(index, contact)" :class="{ 'selected': index == selected }"  >
                <div class="avatar">
                    <img :src="contact.profile_image" :alt="contact.name">
                </div>
                <div class="contact">
                    <p class="name">{{contact.name}}</p>
                    <p class="email">{{contact.email}}</p>
                </div>
            </li>
        </ul>
    </div>
</template>
<script>
export default {
    props: {
        contacts: {
            type: Array,
            default:[]
        }
    },
    data() {
        return {
            selected: 0
        };
    },
    methods: {
        selectContact(index, contact) {
            this.selected = index;
            this.$emit('selected',contact);
        }
    }
}



</script>




<style lang="scss" scoped>
img {
    border-radius: 100%;
}

ul  {
    list-style-type: none;
    padding: 0;

    li.selected {
        background: #afafaf30;;
    }

    li{
        border-bottom: groove;
        border-right: groove;
        border-bottom-width: 1px ;

        padding: 17px;
        display: flex;
        height: 80px;
        position: relative;
        cursor: pointer;



        .avatar {
            padding-right: 20px;
            display: flex;
            align-items: center;


        }

        .avatar img {
            width: 55px;

        }
        .contact {
            font-size: 10px;
            overflow: hidden;
            display: flex;
            flex-direction:column;
            justify-content: center;


            p {
                margin: 0;
            }
        }
    }


}

.contact-list {
    max-height: 500px;
    overflow: scroll;
    max-width: 260px;
}



</style>
