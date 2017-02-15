<template>
  <div
    @mouseover="mouseOver = true"
    @mouseout="mouseOver = false"
    class="color-box"
    :class="{'error': error}"
    :style="{'backgroundColor': color, 'color': fontEndColor}">
    {{ name }}
    <div class="value">{{ color }}</div>
    <div class="tool" :class="{'hidden': !(locked || mouseOver)}">
      <el-row>
        <el-col :span="5" :offset="7">
          <div style="padding: 10px 10px;">
            <el-switch v-model="locked"></el-switch>
          </div>
        </el-col>
        <el-col :span="12">
          <el-row>
            <el-col :span="12">
              <div class="tool-preview" :style="{'backgroundColor': color}"></div>
            </el-col>
            <el-col :span="12">
              <div style="padding: 10px 10px;">
                <el-input size="mini" type="text"  v-model="tempColor"></el-input>
              </div>
              <div style="padding: 0px 10px 10px 10px;">
                <el-input size="mini" type="color" v-model="tempColor"></el-input>
              </div>
            </el-col>
          </el-row>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
import Color from 'color'

const rgex = /(^#[0-9a-fA-F]{3}$)|(^#[0-9a-fA-F]{6}$)/

export default {
  props: {
    name: {
      required: true,
      type: String,
    },
    color: {
      required: true,
      validator (val) {
        return rgex.test(val)
      }
    }
  },
  data () {
    return {
      locked: false,
      mouseOver: false,
      error: false,
      tempColor: ''
    }
  },
  mounted () {
    this.tempColor = this.color
  },
  computed: {
    fontEndColor () {
      return Color(this.color).negate().hex().toString()
    }
  },
  watch: {
    color () {
      this.tempColor = this.color
    },
    tempColor (val) {
      if (rgex.test(val)) {
        this.$emit('colorChange', val)
        this.error = false
      } else {
        this.error = true
      }
    }
  }
}
</script>
