<template>
<span v-if="hasPermission()">
  <slot></slot>
</span>
</template>

<script>
  export default {
    props: {
        'allPermissions': Array,
        'permissionsToBeChecked': {
          type: Array,
          required: true
        },
        'permissionsInStorage': Boolean,
        'permissionsInStorageKey': String
    },

    methods: {
      hasPermission() {
        if (this.permissionsInStorage) {
          return this.checkPermissionsFromStorage();
        } else {
          return this.checkPermissions();
        }
      },

      checkPermissionsFromStorage() {
        let permissions = JSON.parse(localStorage.getItem(this.permissionsInStorageKey));
        if (Array.isArray(permissions)) {
          return this.permissionsToBeChecked.every(permission => permissions.includes(permission));
        } else {
          return false;
        }
      },

      checkPermissions() {
        if (Array.isArray(this.allPermissions) && this.allPermissions.length) {
          return this.permissionsToBeChecked.every(permission => this.allPermissions.includes(permission));
        } else {
          return false;
        }
      }
    }
  }
</script>