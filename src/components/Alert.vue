<template>
  <div class="alertBox">
    <h2>提示</h2>
    <p>確定花費{{ member.price }}元</p>
    <p>成為12個月的{{ member.member }}嗎?</p>
    <div class="btnBlock">
      <button class="btn-cancel"
      @click="clickCancel">
        取消
      </button>
      <button class="btn-buy"
      @click="clickBuy(member)">
        确定
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Alert',
  props: ['member'],
  methods: {
    clickCancel() {
      this.$emit('cancel');
    },
    clickBuy(item) {
      this.$emit('buy', item);
    }
  },
}
</script>