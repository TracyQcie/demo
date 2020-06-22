<template>
  <div class="about">
    <div class="about-navbar">
      <el-page-header v-model="product" @back="goBack" :content="product.title"></el-page-header>
    </div>
    <div class="about-product">
      <el-row type="flex" justify="center">
        <el-col :span="20">
          <div @click="jumpToDetail">
            <el-card :body-style="{ padding: '0px' }" shadow="hover">
              <img :src="product.detailImg" class="image" />
            </el-card>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<style>
.about-product{
  margin: 20px;
}
.el-card.is-hover-shadow:hover {
    box-shadow: -2px 1px 20px 7px rgba(0, 0, 0, 0.28);
}
.el-page-header {
  height: 50px;
  background: #fff;
  display: flex;
  line-height: 24px;
  opacity: 0.7;
}
.el-page-header__title {
  font-size: 14px;
  font-weight: 500;
  line-height: 50px;
}
.el-page-header__content {
  font-size: 18px;
  color: #303133;
  font-weight: 600;
  line-height: 50px;
}
.el-page-header__left {
  display: flex;
  cursor: pointer;
  margin-right: 40px;
  position: relative;
  margin-left: 20px;
}
</style>

<script>
export default {
  name: "Home",
  data() {
    return {
      product: {
        url: "",
        title: "",
        detailUrl: "",
        detailImg: ""
      }
    };
  },
  methods: {
    getDataFromParams: function() {
      if (this.$route.params.product != null) {
        this.product = this.$route.params.product;
      }
    },

    goBack: function() {
      this.$router.go(-1);
      console.log("go back");
    },

    jumpToDetail: function() {
      window.open(this.product.detailUrl);
    }
  },
  created() {
    this.getDataFromParams();
  }
};
</script>