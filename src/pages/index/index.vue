<template>
  <div>
    <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
      style="height:200px"
    >
    <block v-for="item in imgUrls" :key="item">
      <swiper-item>
        <image :src="item" style="width:100%;"/>
      </swiper-item>
    </block>
  </swiper>
  <i-grid i-class="no-border">
      <i-grid-item @click="goList(item.url)" i-class="no-border" v-for="item in grids" :key="item">
          <i-grid-icon>
              <image :src="item.img" />
          </i-grid-icon>
          <i-grid-label>{{item.type}}</i-grid-label>
      </i-grid-item>
  </i-grid>
  <i-panel title="热门路线">
    <view>
      <i-card @click="goType(item.type)" i-class="split" v-for="item in recommand" :key="item" :extra="item.name" :thumb="item.img">
          <view slot="content">路线推荐：{{item.remark}}</view>
          <view slot="footer">最佳季节：{{item.address}}</view>
      </i-card>
    </view>
  </i-panel>
  </div>
</template>

<script>
import card from '@/components/card'
import top from '@/data/top.json'
export default {
  data () {
    return {
      imgUrls: [
        '/static/images/view1.jpg',
        '/static/images/view2.jpg',
        '/static/images/view3.jpg'
      ],
      indicatorDots: true,
      autoplay: true,
      interval: 5000,
      duration: 1000,
      grids: [
        {type:'国家',img:'/static/images/fly.png',"url":'../list/main?type=5'},
        {type:'景点',img:'/static/images/spot.png',"url":'../list/main?type=6'},
        {type:'美食',img:'/static/images/food.png',"url":'../list/main?type=7'},
        {type:'游记',img:'/static/images/hint.png',"url":'../list/main?type=8'},
       
      ],
      recommand: top
    }
  },
  components: {
    card
  },
  methods: {
    goList (url) {
      mpvue.navigateTo({ url })
    },
    goType (type) {
      let url = '../list/main?type=' + type.title
      mpvue.navigateTo({ url })
    }
  },
  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
div >>> .no-border {
  border-width: 0pt;
}
div >>> .split {
  margin-bottom: 10pt;
}
</style>