<template>
  <figure ref="wrapper" class="stage-container figure-vip">
    <div class="stage-wrap">
      <div class="stage" :style="{ transform: `scale(${scale})` }">
        <div class="feature-circle">
          <div class="core">
            <page-icon icon="core" />
          </div>

          <div class="rotator">
            <div v-for="(vipicon, index) in vipicons" :key="index" class="rad">
              <page-icon v-if="vipicon.icon" :icon="vipicon.icon" class="rad-icon" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </figure>
</template>

<script lang="ts">
import { figureMixin } from "./utils"

export default {
  components: {
    "page-icon": () => import("./icon-vip.vue"),
  },
  mixins: [figureMixin({ ref: "wrapper", width: 500 })],
  data() {
    return {
      vipicons: [
        {
          icon: "seo",
        },
        {
          icon: "design",
        },
        {
          icon: "dev",
        },
        {
          icon: "node",
        },
        {
          icon: "github",
        },
        {
          icon: "infrastructure",
        },
        {
          icon: "support",
        },
        {
          icon: "cloud",
        },
      ],
    }
  },
}
</script>

<style lang="less">
figure.figure-vip {
  align-self: center;
  justify-self: center;
  width: 100%;
  height: 100%;
  .stage-wrap,
  .stage {
    width: 100%;
    height: 100%;
  }
  .feature-circle {
    width: 100%;
    height: 100%;
    position: relative;
    transform: rotateY(-5deg);
    transition: all 0.5s;
    @media (max-width: 900px) {
      transform: rotateY(0);
    }

    .rad {
      position: absolute;
      width: 80px;
      height: 80px;
      display: flex;
      align-items: center;
    }
    .core {
      display: grid;
      justify-content: center;
      align-items: center;
      height: 100%;
      height: 100%;
    }
    .rotator {
      position: absolute;
      top: 40%;
      left: 43%;
      @media (max-width: 900px) {
        left: 40%;
      }
    }

    &:hover {
      transform: rotateY(-15deg);
      .rotator {
        transform: rotate(5turn);
        transition: transform 60s cubic-bezier(0.25, 0.1, 0.25, 1);
      }
    }
    .rotator {
      width: 80px;
      height: 80px;
      transform: rotate(2turn);
      transition: transform 1.5s cubic-bezier(0.25, 0.1, 0.25, 1);

      .rad {
        .rad-icon {
          width: 100%;
          height: 100%;
          background: #1b223c;
          box-shadow: 0px 4px 1px rgba(255, 255, 255, 0.16),
            inset 0px 4px 0px rgba(0, 0, 0, 0.42);
          border-radius: 50%;
        }
        &:nth-child(1) {
          transform: rotate(45deg);
          .rad-icon {
            transform: translateY(12rem) rotate(-45deg);
          }
        }
        &:nth-child(2) {
          transform: rotate(90deg);
          .rad-icon {
            transform: translateY(12rem) rotate(-90deg);
          }
        }
        &:nth-child(3) {
          transform: rotate(135deg);
          .rad-icon {
            transform: translateY(12rem) rotate(-135deg);
          }
        }
        &:nth-child(4) {
          transform: rotate(180deg);
          .rad-icon {
            transform: translateY(12rem) rotate(-180deg);
          }
        }
        &:nth-child(5) {
          transform: rotate(225deg);
          .rad-icon {
            transform: translateY(12rem) rotate(-225deg);
          }
        }
        &:nth-child(6) {
          transform: rotate(270deg);
          .rad-icon {
            transform: translateY(12rem) rotate(-270deg);
          }
        }
        &:nth-child(7) {
          transform: rotate(315deg);
          .rad-icon {
            transform: translateY(12rem) rotate(-315deg);
          }
        }
        &:nth-child(8) {
          transform: rotate(0deg);
          .rad-icon {
            transform: translateY(12rem) rotate(-0deg);
          }
        }
      }
    }
  }

  @media (max-width: 900px) {
    height: 420px;
    margin: 2rem 0;
  }
}
</style>
