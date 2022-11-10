<template>
    <h1>Halaman Form Kontak</h1>
    <div id="penampungForm">
        <Form />
    </div>
</template>

<script>

import Form from '@/components/Form.vue';

export default {
    name: 'KontakBaru',
    components: {
        Form
    },
};

</script>

<style>
#penampungForm {
    padding: 20px;
}
</style>