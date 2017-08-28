<template>
  <div class="dashboard-container">
    <div class='dashboard-text'>管理员:{{name}}</div>
    <div class='dashboard-text'>权限:  <span v-for='role in roles' :key='role'>{{role}}</span></div>
  </div>
</template>

<script>
    import { mapGetters } from 'vuex';

    export default {
      name: 'dashboard',
      data() {
        return {
        }
      },
      computed: {
        ...mapGetters([
          'name',
          'roles'
        ])
      },
      created() {
      }
    }
</script>

<style rel="stylesheet/scss" lang="scss">
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
