<script lang="ts" setup>
import { useUserStore } from '@/store'
import { Male, Female } from '@icon-park/vue-next'
const store = useUserStore()
</script>

<template>
  <section class="account-card">
    <div class="card-header">
      <n-avatar round class="avatar" :size="80" :src="store.avatar" />

      <div class="nickname text-ellipsis">
        {{ store.nickname || '未设置昵称' }}
      </div>

      <div class="gender" v-show="store.gender > 0">
        <n-icon v-if="store.gender == 1" :component="Male" color="#ffffff" />
        <n-icon v-if="store.gender == 2" :component="Female" color="#ffffff" />
      </div>
    </div>

    <div class="card-main">
      <div class="usersign pointer">
        <span style="font-weight: 600">个性签名：</span>
        <span>
          {{ store.motto || ' 编辑个签，展示我的独特态度。' }}
        </span>
      </div>
    </div>
  </section>
</template>

<style lang="less" scoped>
.account-card {
  width: 320px;
  min-height: 100px;
  background: var(--im-bg-color);
  padding-bottom: 20px;

  .card-header {
    width: 100%;
    height: 180px;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #0084ff;
    overflow: hidden;

    &::before {
      width: 150px;
      height: 150px;
      content: '';
      background: linear-gradient(to right, #1890ff, #0084ff);
      position: absolute;
      z-index: 1;
      border-radius: 50%;
      right: -25%;
      top: -25%;
    }

    &::after {
      width: 150px;
      height: 150px;
      content: '';
      background: linear-gradient(to left, #1890ff, #0084ff);
      position: absolute;
      z-index: 1;
      border-radius: 50%;
      left: -25%;
      bottom: -20%;
    }

    .gender {
      width: 20px;
      height: 20px;
      position: absolute;
      right: 112px;
      bottom: 46px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
    }

    .nickname {
      position: absolute;
      bottom: 10px;
      width: 50%;
      height: 30px;
      font-size: 16px;
      line-height: 30px;
      text-align: center;
      color: #ffffff;
    }
  }
}

.account-card .card-main {
  margin-top: 10px;
  min-height: 50px;
  text-align: left;
  padding: 0 16px;

  .usersign {
    min-height: 26px;
    border-radius: 5px;
    padding: 8px;
    line-height: 25px;
    background: #f3f5f7;
    color: var(--im-text-color);
    font-size: 12px;
    margin-bottom: 3px;
    position: relative;
  }
}

html[theme-mode='dark'] {
  .account-card .card-header {
    background: #2c2c32;
  }

  .account-card .card-main .usersign {
    background-color: #2c2c32;
  }
}
</style>
