<template>
      <TheFooter>
        <div>
          <!--footer-->
          <a href="https://coreui.io">InDay</a>
          <span class="ml-1">&copy; 2019.</span>
        </div>
      </TheFooter>
</template>
<script>
import { Footer as TheFooter } from '@coreui/vue'
export default {
  name: 'DefaultFooter',
  components: {
    TheFooter
  },
}
</script>
