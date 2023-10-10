<template>
    <div class="page">
        <h4>Thêm liên hệ</h4>
        <ContactFormAdd @submit:contact="create" />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactFormAdd from "@/components/ContactFormAdd.vue";
import ContactService from "@/services/contact.service";

export default {
    components: {
        ContactFormAdd,
    },
    data() {
        return {
            contact: null,
            message: "",
        };
    },
    methods: {
        async create(data) {
            try {
                await ContactService.create(data);
                this.message = "Tạo liên hệ thành công.";
                // Object
                // let myTarget = JSON.parse(JSON.stringify(data))
            } catch (error) {
                console.log(error);
            }
        },
    },

};
</script>