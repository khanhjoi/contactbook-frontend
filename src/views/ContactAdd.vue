<template>
    <div class="page">
        <h4>Thêm mới liên hệ</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="submitContact"
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
// gọi components form để kết nối
import ContactForm from "@/components/ContactForm.vue";

// gọi hàm để kết nói với server
import ContactService from "@/services/contact.service";
export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: {},
            message: "",
        };
    },
    methods: {
        async submitContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Liên hệ được thêm thành công.";
            } catch (error) {
                console.log(error);
            }
        }
    },
    
};
</script>