<template>
  <nav class="subnav-inner">
    <h3>{{ title }}</h3>
    <ul>
      <li
        @click="() => nav('active')"
        v-bind:class="[ current === 'active' ? 'active' : '' ]"
      >
        <i class="subnav-icon">
          <mo-icon name="task-start" width="20" height="20" />
        </i>
        <span>下载中</span>
      </li>
      <li
        @click="() => nav('waiting')"
        v-bind:class="[ current === 'waiting' ? 'active' : '' ]"
      >
        <i class="subnav-icon">
          <mo-icon name="task-pause" width="20" height="20" />
        </i>
        <span>已暂停</span>
      </li>
      <li
        @click="() => nav('stopped')"
        v-bind:class="[ current === 'stopped' ? 'active' : '' ]"
      >
        <i class="subnav-icon">
          <mo-icon name="task-stop" width="20" height="20" />
        </i>
        <span>已完成</span>
      </li>
    </ul>
  </nav>
</template>

<script>
  import '@/components/Icons/task-start'
  import '@/components/Icons/task-pause'
  import '@/components/Icons/task-stop'

  export default {
    name: 'mo-task-subnav',
    props: {
      current: {
        type: String,
        default: 'active'
      }
    },
    computed: {
      title: function () {
        return '任务列表'
      }
    },
    methods: {
      nav: function (status = 'active') {
        console.log('nav status===>', status)
        this.$router.push({
          path: `/task/${status}`
        })
      }
    }
  }
</script>

<style lang="scss">
</style>
