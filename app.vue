<template>
  <div>
    {{ supabase }}
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()
</script>
