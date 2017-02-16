<template>
  <div id="app">
    <header>
      <h1>Element-color</h1>
    </header>
    <section class="content">
      <h2>Color 色彩</h2>
      <p>Element 为了避免视觉传达差异，使用一套特定的调色板来规定颜色，为你所搭建的产品提供一致的外观视觉感受。</p>
      <p>Element-color 则让调色的过程更加直观方便，像魔法一样。</p>
      <h3>主色</h3>
      <p>Element 主要品牌颜色是鲜艳、友好的蓝色。</p>
      <el-row :gutter="12">
        <el-col :span="8">
          <color-box name="Light Primary" :color="lightPrimary" @colorChange="colorChange('lightPrimary', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Primary" :color="primary" @colorChange="colorChange('primary', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Dark Primary" :color="darkPrimary" @colorChange="colorChange('darkPrimary', $event)"></color-box>
        </el-col>
      </el-row>
      <h3>辅助色</h3>
      <p>除了主色外的场景色，需要在不同的场景中使用（例如危险色表示危险的操作）。</p>
      <el-row :gutter="12" style="margin-bottom: 5px;">
        <el-col :span="8">
          <color-box name="Success" :color="success" @colorChange="colorChange('success', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Warning" :color="warning" @colorChange="colorChange('warning', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Danger" :color="danger" @colorChange="colorChange('danger', $event)"></color-box>
        </el-col>
      </el-row>
      <el-row :gutter="12">
        <el-col :span="8">
          <color-box name="Info" :color="info" @colorChange="colorChange('info', $event)"></color-box>
        </el-col>
      </el-row>
      <h3>中性色</h3>
      <p>中性色用于文本、背景和边框颜色。通过运用不同的中性色，来表现层次结构。</p>
      <el-row :gutter="12" style="margin-bottom: 5px;">
        <el-col :span="8">
          <color-box name="Base Black" :color="baseBlack" @colorChange="colorChange('baseBlack', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Base White" :color="baseWhite" @colorChange="colorChange('baseWhite', $event)"></color-box>
        </el-col>
      </el-row>
      <el-row :gutter="12" style="margin-bottom: 5px;">
        <el-col :span="8">
          <color-box name="Black" :color="black" @colorChange="colorChange('black', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Light Black" :color="lightBlack" @colorChange="colorChange('lightBlack', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Extra Light Black" :color="extraLightBlack" @colorChange="colorChange('extraLightBlack', $event)"></color-box>
        </el-col>
      </el-row>
      <el-row :gutter="12" style="margin-bottom: 5px;">
        <el-col :span="8">
          <color-box name="Silver" :color="silver" @colorChange="colorChange('silver', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Light Silver" :color="lightSilver" @colorChange="colorChange('lightSilver', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Extra Light Silver" :color="extraLightSilver" @colorChange="colorChange('extraLightSilver', $event)"></color-box>
        </el-col>
      </el-row>
      <el-row :gutter="12" style="margin-bottom: 5px;">
        <el-col :span="8">
          <color-box name="Gray" :color="gray" @colorChange="colorChange('gray', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Light Gray" :color="lightGray" @colorChange="colorChange('lightGray', $event)"></color-box>
        </el-col>
        <el-col :span="8">
          <color-box name="Extra Light Gray" :color="extraLightGray" @colorChange="colorChange('extraLightGray', $event)"></color-box>
        </el-col>
      </el-row>
      <el-row :gutter="12" style="margin-bottom: 5px;">
        <el-col :span="8">
          <color-box name="Dark White" :color="darkWhite" @colorChange="colorChange('darkWhite', $event)"></color-box>
        </el-col>
      </el-row>
      <h3>色值生成规则</h3>
      <p>Primary 独立指定</p>
      <p>Light Primary 、Dark Primary 派生自 Primary</p>
      <p>Success 、Warning 、Danger 独立指定</p>
      <p>Base Black 、Base White 独立指定</p>
      <p>Black 、Silver 、Gray 派生自 Primary</p>
      <p>Light Black 、Extra Light Black ，Light Silver 、Extra Light Silver ，Light Gray、Extra Light Gray 派生自 Black</p>
      <p>Dark White 派生自 Primary 和 Base White</p>
      <h3>注意</h3>
      <p>派生规则会带来连锁反应。</p>
      <p>每个颜色都可独立指定。</p>
      <p>命名中的颜色单词仅仅是变量名，没有实际色值含义。</p>
      <p>调好颜色后可写到 element theme 的颜色配置中使用。推荐直接写16进制值，配合工具使用更加灵活。</p>
      <h3>工程地址</h3>
      <p><a href="https://github.com/MIKUScallion/element-color" target="_blank">https://github.com/MIKUScallion/element-color</a></p>
    </section>
    <footer></footer>
  </div>
</template>

<script>
import Color from 'color'
import ColorBox from './ColorBox.vue'

export default {
  data () {
    return {
      lightPrimary: '#58B7FF',
      primary: '#20A0FF',
      darkPrimary: '#1D8CE0',

      info: '#50bfff',
      success: '#13CE66',
      warning: '#F7BA2A',
      danger: '#FF4949',

      baseBlack: '#000',
      baseWhite: '#fff',

      black: '#1F2D3D',
      lightBlack: '#324057',
      extraLightBlack: '#475669',

      silver: '#8492A6',
      lightSilver: '#99A9BF',
      extraLightSilver: '#C0CCDA',

      gray: '#D3DCE6',
      lightGray: '#E5E9F2',
      extraLightGray: '#EFF2F7',

      darkWhite: '#F9FAFC'
    }
  },
  mounted () {
    // init
    this.buildDarkPrimary()
    this.buildLightPrimary()

    this.buildBlack()
    this.buildSilver()
    this.buildGray()

    this.buildDarkWhite()

    this.buildDarkWhite()

    this.buildLightBlack()
    this.buildExtraLightBlack()

    this.buildLightSilver()
    this.buildExtraLightSilver()

    this.buildLightGray()
    this.buildExtraLightGray()
  },
  watch: {
    primary () {
      this.buildDarkPrimary()
      this.buildLightPrimary()

      this.buildBlack()
      this.buildSilver()
      this.buildGray()

      this.buildDarkWhite()
    },
    baseWhite () {
      this.buildDarkWhite()
    },
    black () {
      this.buildLightBlack()
      this.buildExtraLightBlack()

      this.buildLightSilver()
      this.buildExtraLightSilver()

      this.buildLightGray()
      this.buildExtraLightGray()
    }
  },
  methods: {
    buildDarkPrimary () {
      const hsl = Color(this.primary).hsl()
      hsl.color[1] = 99
      hsl.color[2] = hsl.color[2] * 0.9
      this.darkPrimary = hsl.hex().toString()
    },

    buildLightPrimary () {
      const hsl = Color(this.primary).hsl()
      hsl.color[1] = 99
      hsl.color[2] = hsl.color[2] * 1.19
      this.lightPrimary = hsl.hex().toString()
    },


    buildBlack () {
      const hsl = Color(this.primary).hsl()
      hsl.color[0] += 6
      hsl.color[1] = 33
      hsl.color[2] = 18
      this.black = hsl.hex().toString()
    },
    buildLightBlack () {
      const hsl = Color(this.black).hsl()
      hsl.color[0] += 5
      hsl.color[1] = 27
      hsl.color[2] = 27
      this.lightBlack = hsl.hex().toString()
    },
    buildExtraLightBlack () {
      const hsl = Color(this.black).hsl()
      hsl.color[0] += 2
      hsl.color[1] = 19
      hsl.color[2] = 35
      this.extraLightBlack = hsl.hex().toString()
    },

    buildSilver () {
      const hsl = Color(this.primary).hsl()
      hsl.color[0] += 3
      hsl.color[1] = 16
      hsl.color[2] = 58
      this.silver = hsl.hex().toString()
    },
    buildLightSilver () {
      const hsl = Color(this.black).hsl()
      hsl.color[0] += 3
      hsl.color[1] = 23
      hsl.color[2] = 67
      this.lightSilver = hsl.hex().toString()
    },
    buildExtraLightSilver () {
      const hsl = Color(this.black).hsl()
      hsl.color[0] += 0
      hsl.color[1] = 26
      hsl.color[2] = 80
      this.extraLightSilver = hsl.hex().toString()
    },

    buildGray () {
      const hsl = Color(this.primary).hsl()
      hsl.color[0] += 0
      hsl.color[1] = 28
      hsl.color[2] = 86
      this.gray = hsl.hex().toString()
    },
    buildLightGray () {
      const hsl = Color(this.black).hsl()
      hsl.color[0] += 10
      hsl.color[1] = 33
      hsl.color[2] = 92
      this.lightGray = hsl.hex().toString()
    },
    buildExtraLightGray () {
      const hsl = Color(this.black).hsl()
      hsl.color[0] += 6
      hsl.color[1] = 33
      hsl.color[2] = 95
      this.extraLightGray = hsl.hex().toString()
    },

    buildDarkWhite () {
      this.darkWhite = Color(this.baseWhite).mix( Color(this.primary), 0.98).hex().toString()
    },
    colorChange (key, color) {
      this[key] = color
      return true
    }
  },
  components: {
    ColorBox
  }
}
</script>

<style>
  :root {
    font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;
    min-width: 1280px;
  }
  body {
    margin: 0px;
  }
  h1, h2, h3 {
    font-weight: 400;
  }
  h1 {
    font-size: 32px;
  }
  h2 {
    font-size: 28px;
  }
  h3 {
    font-size: 22px;
  }

  header {
    height: 80px;
    padding: 0px 30px;
    background-color: #20A0FF;
  }
  header h1 {
    margin: 0px;
    line-height: 80px;
    color: white;
  }
  footer {
    height: 120px;
    background-color: #324057;
    color: #a4aebd;
  }
  .content {
    padding: 55px 30px 95px 30px;
  }
  .content h2 {
    color: #1f2f3d;
  }
  .content p {
    font-size: 14px;
    color: #5e6d82;
  }
  .content h3 {
    margin: 45px 0 15px;
    color: #1f2f3d;
  }

  .color-box {
    position: relative;
    border-radius: 4px;
    padding: 20px;
    height: 74px;
    box-sizing: border-box;
    /*  */
    color: #fff;
    font-size: 14px;
    overflow: hidden;
    /*  */
    border: 1px solid #e0e6ed
  }
  .color-box.error {
    /*  */
    border: 1px solid #FF4949;
  }
  .color-box .value {
    font-size: 12px;
    opacity: 0.69;
    line-height: 24px;
  }
  .color-box .tool {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 1000;
    background-color: rgba(0, 0, 0, 0.3);
    display: block;
  }
  .color-box .tool.hidden {
    opacity: 0;
    width: 0px;
    height: 0px;
    overflow: hidden;
  }
  .tool-preview {
    height:52px;
    margin: 10px;
    /*  */
    border: 1px solid #e0e6ed;
    border-radius: 4px;
  }
</style>
