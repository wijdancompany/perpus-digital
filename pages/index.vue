<template>
  <div>
    <h2>Riwayat Pengunjung</h2>
    <nuxt-link to="/tambah">Isi Kunjungan</nuxt-link>
    <table border="1" width="50%">
      <thead>
        <tr>
          <th>#</th>
          <th>TGL & WAKTU</th>
          <th>NAMA</th>
          <th>ANGGOTA</th>
          <th>KEPERLUAN</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="pengunjung in visitors" :key="pengunjung.id">
          <td>{{ pengunjung.id }}</td>
          <td>{{ pengunjung.tanggal }}</td>
          <td>{{ pengunjung.nama }}</td>
          <td>{{ pengunjung.anggota }}</td>
          <td>{{ pengunjung.keperluan }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const client = useSupabaseClient()
const visitors = ref([])

async function getData() {
  const { data, error } = await client
    .from('pengunjung')
    .select('*')
  if(data) visitors.value = data
}

onMounted(() => getData())
</script>