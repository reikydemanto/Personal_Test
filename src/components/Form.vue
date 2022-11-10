<template>
    <table>
        <tr>
            <td>Nama Lengkap</td>
            <td><input type="text" placeholder="Nama Lengkap" v-model="namaLengkap"></td>
        </tr>
        <tr>
            <td>No Telepon</td>
            <td><input type="number" placeholder="No Telepon" v-model="noTelepon"></td>
        </tr>
        <tr>
            <td>Email</td>
            <td><input type="email" placeholder="Email" v-model="email"></td>
        </tr>
        <tr>
            <td>Alamat</td>
            <td><input type="text" placeholder="Alamat" v-model="alamat"></td>
        </tr>
        <tr>
            <td colspan="2">
                <Button @click="submitData">Submit</Button>
            </td>
        </tr>
    </table>
</template>

<script>

export default {
    name: 'Form',
    data() {
        return {
            namaLengkap: "",
            noTelepon: "",
            email: "",
            alamat: "",
            dataform: []
        }
    },
    methods: {
        submitData() {
            if (!this.namaLengkap && !this.noTelepon && !this.email && !this.alamat) {
                return;
            }

            const a = JSON.parse(localStorage.getItem('daftarkontak')) || []
            if (!a) {
                this.dataform.push({ id: 1, nama: this.namaLengkap, telepon: this.noTelepon, email: this.email, alamat: this.alamat })
            } else {
                this.dataform.push({ id: a[a.length - 1].id+1, nama: this.namaLengkap, telepon: this.noTelepon, email: this.email, alamat: this.alamat })
            }

            this.namaLengkap = ''
            this.noTelepon = ''
            this.email = ''
            this.alamat = ''

            localStorage.setItem('daftarkontak', JSON.stringify(this.dataform))
        }
    }, mounted() {
        if (localStorage.getItem('daftarkontak')) {
            try {
                this.dataform = JSON.parse(localStorage.getItem('daftarkontak'));
            } catch (e) {
                localStorage.removeItem('daftarkontak')
            }
        }
    }
};

</script>

<style>
th {
    padding: 6px;
    width: 25%;
}

td {
    padding: 8px;
}

table {
    margin: 0 auto;
}
</style>