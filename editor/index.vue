<template>
  <div class="component-editor">
    <el-collapse accordion value="1">
      <el-collapse-item title="设置" name="1">
        <div class="list-box">
          <ul>
            <li v-for="item in defaultType" :key="item.value">
              <img :src="item.src" @click="componentInfo.type = item.value">
            </li>
          </ul>
        </div>
        <el-form size="mini">
          <el-form-item label="是否翻转" v-if="componentInfo.type == 'DvBorderBox4' || componentInfo.type == 'DvBorderBox5'">
            <el-select v-model="componentInfo.reverse" placeholder="请选择">
              <el-option label="否" :value="false">
              </el-option>
              <el-option label="是" :value="true">
              </el-option>
            </el-select>
          </el-form-item>
          <el-form-item label='单次动画时长(秒)' v-if="componentInfo.type=='DvBorderBox8'">
            <el-input type='number' v-model.number="componentInfo.dur" placeholder="请输入单次动画时长"></el-input>
          </el-form-item>
          <el-form-item label="标题" v-if="componentInfo.type=='DvBorderBox11'">
            <el-input type="input" v-model="componentInfo.title" placeholder="请输入标题"></el-input>
          </el-form-item>
          <el-form-item label='标题宽度' v-if="componentInfo.type=='Border11'">
            <el-input type='number' v-model.number="componentInfo.titleWidth" placeholder="请输入标题宽度"></el-input>
          </el-form-item>
          <el-form-item label="边框颜色--主颜色">
            <el-color-picker @active-change="changeC1" v-model="componentInfo.comStyle.color1" show-alpha></el-color-picker>
          </el-form-item>
          <el-form-item label="边框颜色--副颜色">
            <el-color-picker @active-change="changeC2" v-model="componentInfo.comStyle.color2" show-alpha></el-color-picker>
          </el-form-item>
        </el-form>
      </el-collapse-item>
    </el-collapse>
  </div>
</template>

<script>
  export default {
    name: 'maliangeditor',
    props: {
      componentInfo: { // 固定字段，收集所有属性值
        type: '',
        reverse: false,
        dur: 3,
        default: {
          comStyle: {
            color1: 'rgb(35, 95, 167)',
              color2: 'rgb(79, 210, 221)'
          }
        }
      }
    },
    data: function () {
      return {
        defaultType: [{
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/8H7gvK_1583807613014.png',
          value: 'DvBorderBox1'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/kovx5P_1583808073400.png',
          value: 'DvBorderBox2'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/ZwEpYb_1583808120473.png',
          value: 'DvBorderBox3'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/MJvEdT_1583808162685.png',
          value: 'DvBorderBox4'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/WzpImB_1583808303617.png',
          value: 'DvBorderBox5'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/hH6U7W_1583808337903.png',
          value: 'DvBorderBox6'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/SMLOm7_1583808396589.png',
          value: 'DvBorderBox7'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/JEkJxb_1583808423561.png',
          value: 'DvBorderBox8'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/eWObAS_1583808459890.png',
          value: 'DvBorderBox9'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/GBtXiq_1583808620211.png',
          value: 'DvBorderBox10'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/wLAKlC_1583808651191.png',
          value: 'DvBorderBox11'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/3jO9vL_1583808715394.png',
          value: 'DvBorderBox12'
        }, {
          src: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/godspenshop/KoLxmw_1583808746102.png',
          value: 'DvBorderBox13'
        }]
      }
    },
    computed: {
    },
    watch: {
      componentInfo: {
        hanlder: function (v) {
          console.log('editor index', v)
        },
      }
    },
    mounted: function () {
    },
    methods: {
      changeC1 (e) {
        this.$set(this.componentInfo.comStyle, 'color1', e)
      },
      changeC2 (e) {
        this.$set(this.componentInfo.comStyle, 'color2', e)
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .component-editor {
    .list-box {
      width 100%
      height 300px
      margin-bottom 10px
      overflow-y scroll
      ul {
        list-style none
        margin 0
        padding-left 0
        li {
          width 100%
          margin-bottom 10px
          cursor pointer
          img {
            width 100%
            height 100%
          }
        }
      }
    }
  }
</style>
