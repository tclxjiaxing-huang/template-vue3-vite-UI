<template>
  <div class="code-show">
    <div class="code-show-example">
      <slot name="example"></slot>
    </div>
    <div class="code-show-content markdown">
      <span class="code-show-content-title" v-text="title"></span>
      <p class="code-show-content-desc">
        <slot name="desc"></slot>
      </p>
      <span @click.native="showCode" class="code-show-content-btn">
        <UpOutlined v-show="!isShow" />
        <DownOutlined v-show="isShow" />
      </span>
    </div>
     <div v-show="isShow" class="code-show-code markdown">
        <slot name="code"></slot>
      </div>
  </div>
</template>

<script>
import { UpOutlined, DownOutlined } from '@ant-design/icons-vue';
export default {
  components: {
    UpOutlined,
    DownOutlined,
  },
  data () {
    return {
      isShow: false
    }
  },
  props: {
    title: String
  },
  methods: {
    showCode () {
      this.isShow = !this.isShow
    }
  }
}
</script>

<style lang="less" scoped>
.code-show {
  position: relative;
  border: 1px solid #dfdfdf;
  border-radius: 4px;
  margin: 12px 0;

  &-example {
    position: relative;
    padding: 42px 20px 50px;

    .ant-menu {
      text-align: left;
    }
  }
  &-content {
    position: relative;
    border-top: 1px solid #dfdfdf;
    padding: 17px 16px 15px 20px;

    &-title {
      position: absolute;
      top: -15px;
      left: 10px;
      padding: 2px 4px;
      background: #fff;
    }

    &-btn {
      position: absolute;
      bottom: 16px;
      right: 16px;
      cursor: pointer;
    }
  }
   &-code {
    position: relative;
    overflow-x: auto;
    margin-right: 1px;
    border-top: 1px dashed #dfdfdf;
    pre {
      background-color: #fff
    }
    .lang-html {
      background-color: #fff
    }
  }
}

</style>
