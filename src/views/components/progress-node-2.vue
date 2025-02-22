<template>
  <div class="flow-card" ref="contentRef">
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
        <div class="flow-card__content-msg-avatar">
          <img class="avatar" src="@/assets/img/test/avatar.png" />
          <img class="avatar" src="@/assets/img/test/avatar.png" />
          <img class="avatar" src="@/assets/img/test/avatar.png" />
          <img class="avatar" src="@/assets/img/test/avatar.png" />
          <div class="flow-card__content-msg-avatar-btn"></div>
        </div>
      </div>
      <div class="flow-card__content-msg open-photo-msg">
        <div class="flow-card__content-msg-hd">
          <div class="hd-point" />
          <span class="hd-text">背景图片</span>
        </div>
        <div class="flow-card__content-msg-upload">
          <img class="upload-bg" src="@/assets/img/test/upload1.png" />
          <div class="upload-text">
            点击上传背景图片
          </div>
        </div>
        <div class="open-photo">
          <div class="open-photo-btn">
            打开图库
          </div>
        </div>
      </div>
      <div class="flow-card__content-msg">
        <div class="flow-card__content-msg-hd">
          <div class="hd-point" />
          <span class="hd-text">背景音乐</span>
        </div>
        <div class="flow-card__content-msg-upload-music">
          <img class="upload-bg" src="@/assets/img/test/upload2.png" />
          <div class="upload-text">
            点击上传背景图片
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
        height,
      } = this.getContentSize();
      node._height = height;
      if (!node.style['style']) {
        node.style['style'] = {};
      }
      node.style['style']['box-shadow'] = '1px 1px 20px 4px rgba(29, 57, 131, 0.05), 0px 4px 10px 0px rgba(29, 57, 131, 0.08)';
    }
  },

  mounted() {
    this.initView();
  }

}
</script>

<style lang="less" scoped>
@import url("@/styles/token.less");

.flow-card {
  border-radius: 6px;
  width: 204px;
  height: 350px;
  background: #FFF;
  position: relative;
  z-index: 10;

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
        margin-bottom: 4px;

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

      &-avatar {
        display: flex;
        gap: 4px;
        position: relative;

        .avatar {
          border-radius: 4px;
          width: 48px;
          height: 48px;
          background: var(--bg, #F0F2F5);
        }

        &-btn {
          width: 12px;
          height: 48px;
          background-color: #FFF;
          background-image: url("@/assets/img/test/button.png");
          background-size: cover;
          background-repeat: no-repeat;
          background-position: center;
          position: absolute;
          right: -8px;
        }
      }



      &-upload {
        display: flex;
        flex-direction: column;
        height: 64px;
        padding: 5px 8px;
        align-items: center;
        align-self: stretch;
        border-radius: 3px;
        border: 1px dashed #DCDCDC;
        background: var(--bg, #F0F2F5);

        .upload-bg {
          width: 24px;
          height: 24px;
        }

        .upload-text {
          color: var(--text-icon-font-gy-340-placeholder, rgba(0, 0, 0, 0.40));
          text-align: center;
          text-overflow: ellipsis;
          white-space: nowrap;
          font-family: "PingFang SC";
          font-size: 10px;
          font-style: normal;
          font-weight: 400;
          line-height: 22px;
          /* 220% */
        }
      }

      &-upload-music {
        display: flex;
        padding: 5px 8px;
        justify-content: center;
        align-items: center;
        gap: 8px;
        flex: 1 0 0;
        align-self: stretch;
        border-radius: 3px;
        border: 1px dashed #DCDCDC;
        background: var(--bg, #F0F2F5);

        .upload-bg {
          width: 24px;
          height: 24px;
        }

        .upload-text {
          color: var(--text-icon-font-gy-340-placeholder, rgba(0, 0, 0, 0.40));
          text-align: center;
          text-overflow: ellipsis;
          white-space: nowrap;
          font-family: "PingFang SC";
          font-size: 10px;
          font-style: normal;
          font-weight: 400;
          line-height: 22px;
          /* 220% */
        }
      }
    }
  }
}

.open-photo {
  &-msg {
    position: relative;
  }

  position: absolute;
  top: 0;
  right: 0;

  &-btn {
    background-color: #FFF2FB;
    display: flex;
    padding: 0px 4px;
    color: #D33691;
    text-align: right;
    font-family: "PingFang SC";
    font-size: 10px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
    /* 200% */
  }
}
</style>
