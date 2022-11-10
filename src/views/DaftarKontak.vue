<template>
    <h1>Halaman Daftar Kontak</h1>
    <div id="penampungTable">
        <TableKontak />
    </div>
</template>

<script>

import TableKontak from '../components/TableKontak.vue'

export default {
    name: 'DaftarKontak',
    components: {
        TableKontak
    }
};

</script> 

<style>
#penampungTable {
    padding: 20px;
}
</style>