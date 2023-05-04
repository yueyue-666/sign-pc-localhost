<template>
  <div id="userLayout" :class="['user-layout-wrapper', isMobile && 'mobile']">
    <div class="container">
      <div class="user-layout-lang">
        <!-- <select-lang class="select-lang-trigger" /> -->
      </div>
      <div class="user-layout-content">
        <div class="top">
          <!-- <div class="header">
            <a href="/">
              <img src="~@/assets/logo.png" class="logo" alt="logo" />
              <span class="title">超级签后台</span>
            </a>
          </div>-->
          <div class="desc">{{ $t('layouts.userLayout.title') }}</div>
        </div>

        <router-view />

        <!-- <div class="footer">
          <div class="links">
            <a href="_self">帮助</a>
            <a href="_self">隐私</a>
            <a href="_self">条款</a>
          </div>
          <div class="copyright">Copyright &copy; 2018 vueComponent</div>
        </div>-->
      </div>
    </div>
  </div>
</template>

<script>
import { deviceMixin } from '@/store/device-mixin'
import SelectLang from '@/components/SelectLang'

export default {
  name: 'UserLayout',
  components: {
    SelectLang
  },
  mixins: [deviceMixin],
  mounted() {
    document.body.classList.add('userLayout')
  },
  beforeDestroy() {
    document.body.classList.remove('userLayout')
  }
}
</script>

<style lang="less" scoped>
#userLayout.user-layout-wrapper {
  height: 100%;

  &.mobile {
    .container {
      .main {
        max-width: 368px;
        width: 98%;
      }
    }
  }

  .container {
    width: 100%;
    min-height: 100%;
    // background: #f0f2f5 url(~@/assets/background.png) no-repeat top center;
    // background-size: 100% 100%;
    //padding: 50px 0 84px;
    position: relative;
    background-color: rgb(221, 234, 253);
    background-image: radial-gradient(closest-side, rgb(0, 106, 255), rgba(0, 106, 255, 0)),
      radial-gradient(closest-side, rgb(193, 171, 249), rgba(193, 171, 249, 0)),
      radial-gradient(closest-side, rgb(255, 255, 255), rgba(255, 255, 255, 0)),
      radial-gradient(closest-side, rgb(140, 0, 255), rgba(140, 0, 255, 0));
    background-size: 130vw 130vh, 120vw 120vh, 100vw 150vh, 120vw 130vh;
    background-position: -80vw -80vh, 30vw -20vh, -20vw 20vh, 30vw 20vh;
    background-repeat: no-repeat;
    animation: 15s moiveAnimation infinite;

    .user-layout-lang {
      width: 100%;
      height: 150px;
      line-height: 44px;
      text-align: right;

      .select-lang-trigger {
        cursor: pointer;
        padding: 12px;
        margin-right: 24px;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        font-size: 18px;
        vertical-align: middle;
      }
    }
    @keyframes moiveAnimation {
      0%,
      100% {
        background-size: 130vw 130vh, 120vw 120vh, 100vw 150vh, 120vw 130vh;
        background-position: -80vw -80vh, 30vw -20vh, -20vw 20vh, 30vw 20vh;
      }

      25% {
        background-size: 120vw 120vh, 130vw 150vh, 130vw 120vh, 100vw 110vh;
        background-position: -30vw -30vh, 40vw -10vh, 0vw 10vh, -10vw 20vh;
      }

      50% {
        background-size: 130vw 130vh, 140vw 100vh, 100vw 150vh, 90vw 110vh;
        background-position: 10vw -60vh, 20vw 10vh, 10vw 30vh, 10vw -20vh;
      }

      75% {
        background-size: 140vw 140vh, 100vw 130vh, 100vw 150vh, 130vw 110vh;
        background-position: -70vw -70vh, 0vw -10vh, 30vw -20vh, 20vw 30vh;
      }
    }

    .user-layout-content {
      padding: 32px 0 24px;

      .top {
        text-align: center;

        .header {
          height: 44px;
          line-height: 44px;

          .badge {
            position: absolute;
            display: inline-block;
            line-height: 1;
            vertical-align: middle;
            margin-left: -12px;
            margin-top: -10px;
            opacity: 0.8;
          }

          .logo {
            height: 44px;
            vertical-align: top;
            margin-right: 16px;
            border-style: none;
          }

          .title {
            font-size: 33px;
            color: rgba(0, 0, 0, 0.85);
            font-family: Avenir, 'Helvetica Neue', Arial, Helvetica, sans-serif;
            font-weight: 600;
            position: relative;
            top: 2px;
          }
        }
        .desc {
          font-size: 14px;
          color: rgba(0, 0, 0, 0.45);
          margin-top: 12px;
          margin-bottom: 40px;
        }
      }

      .main {
        background-color: rgba(255, 255, 255, 0.5);
        border-radius: 5px;
        padding: 40px;
        width: 400px;
        min-width: 260px;
        margin: 0 auto;
      }

      .footer {
        // position: absolute;
        width: 100%;
        bottom: 0;
        padding: 0 16px;
        margin: 48px 0 24px;
        text-align: center;

        .links {
          margin-bottom: 8px;
          font-size: 14px;
          a {
            color: rgba(0, 0, 0, 0.45);
            transition: all 0.3s;
            &:not(:last-child) {
              margin-right: 40px;
            }
          }
        }
        .copyright {
          color: rgba(0, 0, 0, 0.45);
          font-size: 14px;
        }
      }
    }

    a {
      text-decoration: none;
    }
  }
}
</style>
