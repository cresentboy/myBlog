<template>
  <div class="share">
    <p class="diggit" @click="praiseBlog(blogUid)">
      <a href="javascript:void(0);">很赞哦！</a>
<<<<<<< HEAD
      <span v-if="praiseCount!= 0">
        (<b id="diggnum">{{praiseCount}}</b>)
      </span>
    </p>
    <p class="dasbox">
      <a href="javascript:void(0)" @click="dashangToggle()" class="dashang" title="打赏，支持一下">打赏本站</a>
    </p>
    <div class="hide_box" v-if="showPay"></div>
    <div class="shang_box" v-if="showPay">
      <a class="shang_close" href="javascript:void(0)" @click="dashangToggle()" title="关闭">关闭</a>
=======
      <span v-if="praiseCount != 0">
        (<b id="diggnum">{{ praiseCount }}</b
        >)
      </span>
    </p>
    <p class="dasbox">
      <a
        href="javascript:void(0)"
        @click="dashangToggle()"
        class="dashang"
        title="打赏，支持一下"
        >打赏本站</a
      >
    </p>
    <div class="hide_box" v-if="showPay"></div>
    <div class="shang_box" v-if="showPay">
      <a
        class="shang_close"
        href="javascript:void(0)"
        @click="dashangToggle()"
        title="关闭"
        >关闭</a
      >
>>>>>>> 64a8ebf (update sth.)
      <div class="shang_tit">
        <p>感谢您的支持，我会继续努力的!</p>
      </div>
      <div class="shang_payimg">
<<<<<<< HEAD
        <img :src="payCode" alt="扫码支持" title="扫一扫">
      </div>
      <div class="pay_explain">扫码打赏，你说多少就多少</div>
      <div class="shang_payselect">
        <div
          class="pay_item"
          :class="[this.payMethod==1?'checked':'']"
=======
        <img :src="payCode" alt="扫码支持" title="扫一扫" />
      </div>
      <div class="pay_explain">扫码打赏</div>
      <div class="shang_payselect">
        <div
          class="pay_item"
          :class="[this.payMethod == 1 ? 'checked' : '']"
>>>>>>> 64a8ebf (update sth.)
          data-id="alipay"
          @click="choosePay('1')"
        >
          <span class="radiobox"></span>
          <span class="pay_logo">
<<<<<<< HEAD
            <img src="../../../static/images/alipay.jpg" alt="支付宝">
=======
            <img src="../../../static/images/alipay.jpg" alt="支付宝" />
>>>>>>> 64a8ebf (update sth.)
          </span>
        </div>
        <div
          class="pay_item"
<<<<<<< HEAD
          :class="[this.payMethod==2?'checked':'']"
=======
          :class="[this.payMethod == 2 ? 'checked' : '']"
>>>>>>> 64a8ebf (update sth.)
          data-id="weipay"
          @click="choosePay('2')"
        >
          <span class="radiobox"></span>
          <span class="pay_logo">
<<<<<<< HEAD
            <img src="../../../static/images/wechat.jpg" alt="微信">
=======
            <img src="../../../static/images/wechat.jpg" alt="微信" />
>>>>>>> 64a8ebf (update sth.)
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { getWebConfig } from "../../api/index";
import {
  praiseBlogByUid,
<<<<<<< HEAD
  getBlogPraiseCountByUid
} from "../../api/blogContent";
import {mapMutations} from "vuex";
=======
  getBlogPraiseCountByUid,
} from "../../api/blogContent";
import { mapMutations } from "vuex";
>>>>>>> 64a8ebf (update sth.)
export default {
  name: "PayCode",
  props: {
    praiseCount: {
      type: Number,
<<<<<<< HEAD
      default: 0
    },
    blogUid: {
      type: String
    }
=======
      default: 0,
    },
    blogUid: {
      type: String,
    },
>>>>>>> 64a8ebf (update sth.)
  },
  data() {
    return {
      webConfigData: [],
      showPay: false, //是否显示支付
      payMethod: 1, // 1: 支付宝  2：微信
      payCode: "", //支付码图片
    };
  },
  created() {
<<<<<<< HEAD
    getWebConfig().then(response => {
      console.log("从接口中获取")
=======
    getWebConfig().then((response) => {
      console.log("从接口中获取");
>>>>>>> 64a8ebf (update sth.)
      if (response.code == this.$ECode.SUCCESS) {
        this.webConfigData = response.data;
        this.payCode = this.webConfigData.aliPayPhoto;
      }
    });
  },
  methods: {
    //拿到vuex中的写的方法
<<<<<<< HEAD
    ...mapMutations(['setLoginMessage']),
    dashangToggle: function() {
      this.showPay = !this.showPay;
    },
    // 支付方式
    choosePay: function(type) {
=======
    ...mapMutations(["setLoginMessage"]),
    dashangToggle: function () {
      this.showPay = !this.showPay;
    },
    // 支付方式
    choosePay: function (type) {
>>>>>>> 64a8ebf (update sth.)
      this.payMethod = type;
      if (type == 1) {
        this.payCode = this.webConfigData.aliPayPhoto;
      } else {
        this.payCode = this.webConfigData.weixinPayPhoto;
      }
    },
    //博客点赞
<<<<<<< HEAD
    praiseBlog: function(uid) {
      // 判断用户是否登录
      let isLogin = this.$store.state.user.isLogin
      if(!isLogin) {
        this.$notify.error({
          title: '警告',
          message: '登录后才可以评论哦~',
          offset: 100
        });
        // 未登录，自动弹出登录框
        this.setLoginMessage(Math.random())
=======
    praiseBlog: function (uid) {
      // 判断用户是否登录
      let isLogin = this.$store.state.user.isLogin;
      if (!isLogin) {
        this.$notify.error({
          title: "警告",
          message: "登录后才可以评论哦~",
          offset: 100,
        });
        // 未登录，自动弹出登录框
        this.setLoginMessage(Math.random());
>>>>>>> 64a8ebf (update sth.)
        return;
      }

      var params = new URLSearchParams();
      params.append("uid", uid);
<<<<<<< HEAD
      praiseBlogByUid(params).then(response => {
        if (response.code == this.$ECode.SUCCESS) {
          this.$notify({
            title: '成功',
            message: "点赞成功",
            type: 'success',
            offset: 100
          });
          this.$emit('update:praiseCount',response.data);
        } else {
          this.$notify.error({
            title: '错误',
            message: response.message,
            offset: 100
=======
      praiseBlogByUid(params).then((response) => {
        if (response.code == this.$ECode.SUCCESS) {
          this.$notify({
            title: "成功",
            message: "点赞成功",
            type: "success",
            offset: 100,
          });
          this.$emit("update:praiseCount", response.data);
        } else {
          this.$notify.error({
            title: "错误",
            message: response.message,
            offset: 100,
>>>>>>> 64a8ebf (update sth.)
          });
        }
      });
    },
    //获取点赞数
<<<<<<< HEAD
    getPraiseCount: function(uid) {
      var params = new URLSearchParams();
      params.append("uid", uid);
      getBlogPraiseCountByUid(params).then(response => {
=======
    getPraiseCount: function (uid) {
      var params = new URLSearchParams();
      params.append("uid", uid);
      getBlogPraiseCountByUid(params).then((response) => {
>>>>>>> 64a8ebf (update sth.)
        if (response.code == this.$ECode.SUCCESS) {
          this.praiseCount = response.data;
        }
      });
<<<<<<< HEAD
    }
  }
=======
    },
  },
>>>>>>> 64a8ebf (update sth.)
};
</script>

<style>
<<<<<<< HEAD
  .diggit {
    cursor: pointer;
  }
=======
.diggit {
  cursor: pointer;
}
>>>>>>> 64a8ebf (update sth.)
</style>
