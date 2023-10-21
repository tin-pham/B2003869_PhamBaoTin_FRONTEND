<template>
  <div class="page">
    <h4>Thêm Liên hệ</h4>
    <ContactForm :contact="contact" @create:contact="createContact" />
    <p>{{ message }}</p>
  </div>
</template>
<script>
import ContactForm from '@/components/ContactForm.vue';
import ContactService from '@/services/contact.service';
export default {
  components: {
    ContactForm,
  },
  data() {
    return {
      contact: {}, // Initialize with an empty object
      message: '',
    };
  },
  created() {
    this.message = '';
  },
  methods: {
    async createContact(data) {
      try {
        await ContactService.create(data);
        this.message = 'Liên hệ được thêm thành công.';
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
