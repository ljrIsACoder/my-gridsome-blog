<template>
  <div class="layout">
    <el-container>
      <el-header class="header" style="height: 400px">
        <div>
          <p class="site-name">{{ $static.metadata.siteName }}</p>
          <p>欢迎来到{{ $static.metadata.siteName }}的个人博客</p>
          <p>
            <el-button @click="toGithub">Github主页</el-button>
            <el-button @click="toSourceCode">博客源码</el-button>
          </p>
        </div>
      </el-header>
      <main class="main">
        <aside class="aside">
          <Menu :menuList="menuList"></Menu>
        </aside>
        <div class="content">
          <slot/>
        </div>
      </main>
    </el-container>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
  import Menu from '../components/Menu'

  export default {
    name: 'Layout',
    components: {
      Menu
    },
    data () {
      return {
        menuList: [
          {
            path: '/',
            title: '最新动态',
            icon: 'el-icon-star-off'
          },
          {
            path: '/posts',
            title: '博客列表',
            icon: 'el-icon-edit-outline'
          },
          {
            path: '/tags',
            title: '标签列表',
            icon: 'el-icon-price-tag'
          },
          {
            path: '/readme',
            title: 'README.md',
            icon: 'el-icon-document'
          },
        ]
      }
    },
    methods: {
      toGithub () {
        location.href = 'https://github.com/ljrIsACoder'
      },
      toSourceCode () {
        location.href = 'https://github.com/ljrIsACoder/my-gridsome-blog'
      }
    }
  }
</script>


<style scoped>
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
}

.layout {
  max-width: 100%;
  margin: 0 auto;
}

.header {
  width: 100%;
  height: 400px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: url('../../static/images/header.jpeg') no-repeat;
  background-size: conver;
}

.header > div {
  margin: 0 auto;
  text-align: center;
}

.header > div > p {
  font-size: 24px;
  color: #fff;
}

.site-name {
  font-size: 36px;
  font-weight: bold;
}

.main {
  width: 1024px;
  margin: 0 auto;
  position: relative;
  top: 20px;
}

.aside {
  width: 220px;
  padding: 20px;
  border: 1px solid #e6e6e6;
  position: absolute;
  top: 0;
  left: 0;
}

.content {
  padding-left: 280px;
}
</style>
