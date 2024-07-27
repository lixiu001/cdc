<template>
  <view>
    <slot></slot>
  </view>
</template>

<script>
export default {
  name: "xs-form",
  components: {},
  options: {
    virtualHost: true
  },
  props: {
    value: {
      type: Object,
      default: () => ({})
    },
    disabled: {
      type: [Boolean, String],
      default: false
    }
  },
  data() {
    return {};
  },
  watch: {
    value(newVal) {
      this.initFormValue(newVal);
    },
  },
  computed: {},
  methods: {
    initFormValue(newVal) {
      let val = newVal || {};
      this.childrens.forEach((item) => {
        let value = val[item.name];
        item.value = value == null ? null : value;
        item.disabled = this.disabled || item.disabled;
      });
    },
    onChange(event, that) {
      let mode = that.pickerProps?.mode;
      let value = event.detail.value;
      that.val = value;
      if (that.type === 'select' && (!mode || mode === 'selector' || mode === 'multiSelector')) {
        let range = that.$props.pickerProps?.range || [];
        value = range[value].key;
      }
      let values = {[that.$props.name]: value};
      this.$emit('onValuesChange', values, {...this.value, ...values});
	  this.$emit('input', {...this.value, ...values})
    },
    validateFields({showError = true} = {}) {
      return new Promise((resolve, reject) => {
        let validate = true;
        let values = {...this.value}
        this.childrens.forEach((item) => {
          let value = item.val;
          let mode = item.pickerProps?.mode;
          if (item.type === 'select' && (!mode || mode === 'selector' || mode === 'multiSelector')) {
            let range = item.$props.pickerProps?.range || [];
            value = value == null ? item.value : range[value].key;
          }
          values[item.name] = value;
          if (validate && item.required && showError && (value === '' || value == null)) {
            validate = false;
            uni.showToast({title: `${item.title}必填`, icon: 'none'});
          }
        })
        validate ? resolve(values) : reject();
      })
    }
  },
  created() {
    this.childrens = [];
  },
  mounted() {
    this.initFormValue(this.value);
  },
  destroyed() {
  },
};
</script>

<style lang="scss">

.componentBox {
  .formItem {
    border-bottom: 1rpx solid #ededed;

    &:last-child {
      border-bottom: none;
    }
  }
}
</style>
<style scoped lang="scss">

.componentBox {
}
</style>
