<template>
  <div id="globalhader">
    <a-row :wrap="false">
      <a-col flex="200px">
        <div class="title-bar">
          <img class="logo" src="../assets/logo.png" alt="logo" />
          <div class="title">去月球用户管理</div>
        </div>
      </a-col>
      <a-col flex="auto"
        ><a-menu
          v-model:selectedKeys="current"
          mode="horizontal"
          :items="items"
          @click="doMenuClick"
      /></a-col>
      <a-col flex="80px">
        <div class="user-login-status">
          <a-button type="primary" href="/user/login">登录</a-button>
        </div>
      </a-col>
    </a-row>
  </div>
</template>
<script lang="ts" setup>
import { h, ref } from "vue";
import { CrownOutlined, HomeOutlined } from "@ant-design/icons-vue";
import { MenuProps } from "ant-design-vue";
import { useRouter } from "vue-router";
const router = useRouter();

const doMenuClick = ({ key }: { key: string }) => {
  router.push({
    path: key,
  });
};
const current = ref<string[]>(["mail"]);
router.afterEach((to, form, failure) => {
  current.value = [to.path];
});
const items = ref<MenuProps["items"]>([
  {
    key: " /",
    icon: () => h(HomeOutlined),
    label: "首页",
    title: "首页",
  },
  {
    key: "/user/login",
    label: "用户登录",
    title: "用户登录",
  },
  {
    key: "/user/register",
    label: "用户注册",
    title: "用户注册",
  },
  {
    key: "/admin/userManage",
    icon: () => h(CrownOutlined),
    label: "用户管理",
    title: "用户管理",
  },

  {
    key: "other",
    label: h(
      "a",
      {
        href: "https://space.bilibili.com/135382614?spm_id_from=333.1007.0.0",
        target: "_blank",
      },
      "去月球"
    ),
    title: "去月球",
  },
]);
</script>
icon: () => h(SettingOutlined),
<style scoped>
.title-bar {
  display: flex;
  align-items: center;
}
.title {
  color: black;
  font-size: 18px;
  margin-left: 16px;
}
.logo {
  height: 32px;
}
</style>
