<template>
    <div v-if="daftarkontak.length">
        <table border="1">
            <tr>
                <th>Nama Lengkap</th>
                <th>Nomor HP</th>
                <th>Email</th>
                <th>Alamat</th>
                <th>Action</th>
            </tr>
            <tr v-for="data in daftarkontak" :key="data.id">
                <td>{{ data.nama }}</td>
                <td>{{ data.telepon }}</td>
                <td>{{ data.email }}</td>
                <td>{{ data.alamat }}</td>
                <td>Update,Delete</td>
            </tr>
        </table>
    </div>
    <div v-else>
        <h3>Mohon Maaf data kosong, silahkan input data terlebih dahulu</h3>
    </div>
</template>

<script>
export default {
    name: 'TableKontak',
    data() {
        return {
            daftarkontak: [],
        }
    },
    created() {
        if (!JSON.parse(localStorage.getItem('daftarkontak'))) {
            console.log("Kosong")
        } else {
            console.log("ada isinya")
            this.daftarkontak = JSON.parse(localStorage.getItem('daftarkontak')) || []
        }
    }
};
</script>

<style>
th {
    padding: 6px;
    width: 20%;
}

td {
    padding: 8px;
}

table {
    margin: 0 auto;
    border: 1px #2c3e50 !important;
    border-collapse: collapse !important;
}
</style>