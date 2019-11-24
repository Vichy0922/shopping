<template>
  <div>
    <view class="userinfo">
    <view class="userinfo-avatar">
    <open-data type="userAvatarUrl"></open-data>
    </view>
    <open-data type="userNickName"></open-data>
    </view>
    <i-panel title="旅行家，写下你的推荐吧">
      <i-input :value="name" @change="changeName($event)" title="景点/美食/攻略" autofocus placeholder="请选择你的推荐内容" maxlength="50" />
      <i-input :value="address" @change="changeAddress($event)" title="推荐详情" placeholder="请写下推荐的具体内容" maxlength="100" />
      <i-input :value="reason" @change="changeReason($event)" title="推荐理由" placeholder="请写下推荐理由" maxlength="100" />
    </i-panel>
    <i-button @click="handleClick" type="info" size="default">我要推荐</i-button>
    <view class="tips">欧洲旅行，期待你的分享和攻略！！！</view>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name:"",
      address:"",
      reason:""
    }
  },
  methods: {
    changeName (event) {
      this.name = event.mp.detail.detail.value
    },
    changeReason (event) {
      this.reason = event.mp.detail.detail.value
    },
    changeAddress (event) {
      this.address = event.mp.detail.detail.value
    },
    handleClick () {
      if (this.name && this.reason && this.address) {
        wx.showToast({
          title: '推荐了' + this.name,
          icon: 'success',
          duration: 2000
        })
        // TODO:将推荐数据提交到云数据库
      } else {
        wx.showToast({
          title: '信息不完整',
          icon: 'none',
          duration: 2000
        })
      }
    }
  },
  created () {
  }
}
</script>

<style scoped>
.userinfo {
  position: relative;
  width: 750rpx;
  height: 320rpx;
  color: #666;
  display: flex;
  flex-direction: column;
  align-items: center;
}
 
.userinfo-avatar {
  overflow:hidden;
  display: block;
  width: 160rpx;
  height: 160rpx;
  margin: 20rpx;
  margin-top: 50rpx;
  border-radius: 50%;
  border: 2px solid #fff;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
}
.tips {
  padding: 20pt;
  font-size: 10pt;
  color:#3366CC;
}
</style>