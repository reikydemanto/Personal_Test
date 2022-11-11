<template>
    <div class="main">
        <div>
            <h3>Yakin ingin menghapus?</h3>
            <button @click="jawabIya">Iyaa</button>
            <button @click="jawabTidak">Tidak</button>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Modal',
    data() {
        return {
            jawaban: ""
        }
    }, methods: {
        jawabIya() {
            this.jawaban = "iya"
            console.log(this.jawaban,"jawaban modal")
            this.$emit("jawaban", this.jawaban)
        }, jawabTidak() {
            this.jawaban = "tidak"
            console.log(this.jawaban,"jawaban modal")
            this.$emit("jawaban", this.jawaban)
        },

    },emits: ["jawaban"]
}

</script>

<style>
.main div {
    background-color: rgba(0, 0, 0, 0.5);
    margin: auto auto;
    width: 40%;
    padding: 40px 40px !important;
}

.main div button {
    padding: 4px;
    width: 80px;
    margin: 12px;
}
</style>