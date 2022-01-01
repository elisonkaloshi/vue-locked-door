<template>
  <div>
    <HasPermission :all-permissions="['view_user', 'edit_user']" :permissions-to-be-checked="['view_user']" :permissions-in-storage="false" :permissions-in-storage-key="'permi'">
      <div>hello</div>
    </HasPermission>

  </div>
</template>

<script>
import HasPermission from "./HasPermission";
export default {
  name: "Test",
  components: {HasPermission}
}
</script>

<style scoped>

</style>