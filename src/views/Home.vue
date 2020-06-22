<template>
  <div class="home">
    <div class="carousel">
      <el-carousel :interval="5000" arrow="hover" type="card" height="fartherHeight + 'px'">
        <el-carousel-item v-for="(item,index) in carouselItems" :key="index">
          <img :src="item.url" class="image" />
        </el-carousel-item>
      </el-carousel>
    </div>
    <div class="product-list">
      <el-row :gutter="20">
        <el-col :span="6" v-for="(product,index) in productList" :key="index">
          <div @click="jumpToAbout(product)">
            <el-card :body-style="{ padding: '0px' }" shadow="hover">
              <img :src="product.url" class="image" />
            </el-card>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<style>
.home {
  padding: 0 50px;
}
.carousel {
  margin: 10px 0;
}
.product-list {
  margin: 20px 0;
}
.el-carousel__item h3 {
  color: #475669;
  font-size: 14px;
  opacity: 0.75;
  line-height: 200px;
  margin: 0;
}

.el-carousel__item:nth-child(2n) {
  background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n + 1) {
  background-color: #d3dce6;
}
img {
  width: 100%;
  height: inherit;
}
</style>

<script>
export default {
  name: "Home",
  data: () => ({
    // 图片父容器高度
    fartherHeight: 1000,
    // 浏览器宽度
    screenWidth: 0,
    carouselItems: [
      {
        url:
          "https://gss0.baidu.com/7LsWdDW5_xN3otqbppnN2DJv/space/pic/item/023b5bb5c9ea15ce7408d252b9003af33b87b282.jpg"
      },
      {
        url:
          "https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1592800315287&di=6a5b8af3f81efa745b4b4d1ff5f9b923&imgtype=0&src=http%3A%2F%2Fp3.ssl.cdn.btime.com%2Ft01d459fc4dca7961e2.jpg%3Fsize%3D1920x1080"
      },
      {
        url:
          "https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1592800315430&di=987e6a58f30a7f0f9478252b40e69100&imgtype=0&src=http%3A%2F%2F5b0988e595225.cdn.sohucs.com%2Fimages%2F20180713%2F60033cf4da4b40e8b1c853617957f25f.jpeg"
      }
    ],
    productList: [
      {
        url:
          "http://cdn.cnbj2.fds.api.mi-img.com/viomi-official/images/website/v2/newviomi/mainscene/zh/list1-1.jpg",
        title: "互联网净水器",
        detailUrl: "https://www.viomi.com.cn/proDetails?skuId=111111",
        detailImg:
          "http://cdn.cnbj2.fds.api.mi-img.com/viomi-official/images/website/v2/proDetails/pc/111111/main.jpg"
      },
      {
        url:
          "http://cdn.cnbj2.fds.api.mi-img.com/viomi-official/images/website/v2/newviomi/mainscene/zh/list1-5.jpg",
        title: "互联网洗碗机",
        detailUrl: "https://www.viomi.com.cn/proDetails?skuId=222222",
        detailImg:
          "http://cdn.cnbj2.fds.api.mi-img.com/viomi-official/images/website/v2/proDetails/pc/222222/1.jpg"
      },
      {
        url:
          "http://cdn.cnbj2.fds.api.mi-img.com/viomi-official/images/website/v2/newviomi/mainscene/zh/list1-3.jpg",
        title: "互联网油烟机",
        detailUrl: "https://www.viomi.com.cn/proDetails?skuId=2018030303",
        detailImg:
          "http://cdn.cnbj2.fds.api.mi-img.com/viomi-official/images/website/v2/proDetails/pc/2018030303/main.jpg"
      },
      {
        url:
          "http://cdn.cnbj2.fds.api.mi-img.com/viomi-official/images/website/v2/newviomi/mainscene/zh/list1-2.jpg",
        title: "互联网冰箱",
        detailUrl: "https://www.viomi.com.cn/proDetails?skuId=2018030301",
        detailImg:
          "http://cdn.cnbj2.fds.api.mi-img.com/viomi-official/images/website/v2/proDetails/pc/2018030301/main.jpg"
      }
    ]
  }),

  methods: {
    /**  轮播图自适应函数 */
    setSize: function() {
      // 通过浏览器宽度(图片宽度)计算高度
      this.bannerHeight = (400 / 1920) * this.screenWidth;
    },
    /** 跳转详情页 */
    jumpToAbout: function(product) {
      console.log("nihao");
      this.$router.push({
        path: "/about",
        name: "About",
        params: {
          product: product
        }
      });
    }
  },
  mounted() {
    // 首次加载时,需要调用一次自适应函数
    this.screenWidth = window.innerWidth;
    this.setSize();
    // 窗口大小发生改变时,再调用一次
    window.onresize = () => {
      this.screenWidth = window.innerWidth;
      this.setSize();
    };
  }
};
</script>


