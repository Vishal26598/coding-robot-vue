<template>
  <div>
    <OuterCard></OuterCard>
  </div>
</template>

<script>
// @ is an alias to /src
import OuterCard from '@/components/OuterCard.vue'

export default {
  name: 'Home',
  components: {
    OuterCard
  }
}
</script>
