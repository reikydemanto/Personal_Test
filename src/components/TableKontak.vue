<template>
    <div v-if="editor.length">
        <table>
            <tr>
                <td>Nama Lengkap</td>
                <td><input type="text" placeholder="Nama Lengkap" v-model="namaLengkap"></td>
            </tr>
            <tr>
                <td>No Telepon</td>
                <td><input type="text" placeholder="No Telepon" v-model="noTelepon"></td>
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
                    <Button @click="tombolUpdateData">Submit</Button>
                </td>
            </tr>
        </table>
    </div>
    <div v-else>
        <div v-if="daftarkontak.length">
            <table border="1">
                <tr>
                    <th>Nama Lengkap</th>
                    <th>Nomor HP</th>
                    <th>Email</th>
                    <th>Alamat</th>
                    <th>Action</th>
                </tr>
                <tr v-for="(value, key) in daftarkontak">
                    <td>{{ value.nama }}</td>
                    <td>{{ value.telepon }}</td>
                    <td>{{ value.email }}</td>
                    <td>{{ value.alamat }}</td>
                    <td>
                        <button @click="updateData(key,value.id,value.nama,value.telepon,value.email,value.alamat)">Update</button>
                        <button @click="deleteData(key)">Delete</button>
                    </td>
                </tr>
            </table>
        </div>
        <div v-else>
            <h3>Mohon Maaf data kosong, silahkan input data terlebih dahulu</h3>
        </div>
    </div>
</template>

<script>

export default {
    name: 'TableKontak',
    data() {
        return {
            daftarkontak: [],
            editor: [],
            namaLengkap: "",
            noTelepon: "",
            email: "",
            alamat: "",
            keyss: "",
            id: ""
        }
    },
    methods: {
        deleteData(key) {
            this.daftarkontak.splice(key, 1);
            localStorage.setItem('daftarkontak', JSON.stringify(this.daftarkontak))
        }, updateData(keysss,idsss,namalengk,notelep,emai,alama) {
            this.editor = [1]
            this.namaLengkap = namalengk
            this.noTelepon = notelep
            this.email = emai
            this.alamat = alama
            this.keyss = keysss
            this.id = idsss
        }, tombolUpdateData(){
            
            if (!this.namaLengkap && !this.noTelepon && !this.email && !this.alamat) {
                return;
            }

            this.daftarkontak.splice(this.keyss, 1);
            localStorage.setItem('daftarkontak', JSON.stringify(this.daftarkontak))

            this.daftarkontak.push({ id: this.id, nama: this.namaLengkap, telepon: this.noTelepon, email: this.email, alamat: this.alamat })
            localStorage.setItem('daftarkontak', JSON.stringify(this.daftarkontak))
            this.editor = ""
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