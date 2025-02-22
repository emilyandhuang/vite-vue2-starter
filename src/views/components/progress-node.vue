<template>
  <div class="flow-card-container" ref="contentRef">
    <div class="flow-card">
      <!-- 头部区域 -->
      <div class="flow-card__header">
        <img class="flow-card__header-icon" src="@/assets/img/test/hd-icon.png" />
        <span class="flow-card__header-text">场景配置卡片</span>
      </div>
      <!-- 内容区域 -->
      <div class="flow-card__content">
        <div class="flow-card__content-input">
          <!-- <textarea class="flow-card__content-input-control" /> -->
          <span class="flow-card__content-input-placeholder">配置此节点场景的角色，背景图片和音乐。（仅适配沉浸式网页）</span>
        </div>
        <div class="flow-card__content-msg">
          <div class="flow-card__content-msg-hd">
            <div class="hd-point" />
            <span class="hd-text">角色设置</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProgressNode',
  inject: ['getNode', 'getGraph'],
  data() {
    return {
      percentage: 80,
    }
  },
  methods: {
    getContentSize() {
      const { contentRef: element } = this.$refs
      return {
        width: element.offsetWidth,
        height: element.offsetHeight,
      };
    },
    initView() {
      const node = this.getNode();
      console.log('执行了', node);
      const {
        width,
        height,
      } = this.getContentSize();
      node.width = width;
      node.height = height;
    }
  },

  mounted() {
    this.initView();
    console.log(this.$attrs)
  }

}
</script>

<style lang="less" scoped>
@import url("@/styles/token.less");

.flow-card-container {
  width: 100%;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.flow-card {
  border-radius: 6px;
  width: 204px;
  height: calc(100% - 20px);
  background: #FFF;
  position: relative;
  z-index: 10;
  box-shadow: 1px 1px 20px 4px rgba(29, 57, 131, 0.05), 0px 4px 10px 0px rgba(29, 57, 131, 0.08);

  &__header {
    display: flex;
    padding: 8px;

    &-icon {
      width: 20px;
      height: 20px;
    }

    &-text {
      .title-small;
      margin-left: 4px;
    }
  }

  &__content {
    padding: 8px 8px 12px 8px;
    display: flex;
    flex-direction: column;
    gap: 8px;

    &-input {
      position: relative;
      padding: 2px 4px;

      &-control {
        width: 100%;
        height: 100%;
      }

      &-placeholder {
        color: var(--font-icon-gy-3-placeholder, rgba(0, 0, 0, 0.40));
        font-family: "PingFang SC";
        font-size: 12px;
        font-style: normal;
        font-weight: 400;
        line-height: 20px;
        /* 166.667% */
      }
    }

    &-msg {
      &-hd {
        display: flex;
        align-items: center;

        .hd {
          &-point {
            width: 6px;
            height: 6px;
            background-color: #D33691;
            border-radius: 50%;
          }

          &-text {
            .mark-small;
            margin-left: 4px;
          }
        }
      }
    }
  }
}
</style>
