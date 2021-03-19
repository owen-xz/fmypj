<template>
  <div class="content">
    <div class="member-now"
    :style="{backgroundImage: `url(${nowMember.bg})`}">
      <div class="mask">
        <img class="icon" :src="nowMember.icon" alt="">
        <img class="logo" src="../assets/img/1887.svg" alt="">
        <h1>{{ nowMember.member }}</h1>
        <h4>{{ nowMember.detail}}</h4>
        <h4 class="deadline">2020.08.11止</h4>
      </div>
    </div>
    <ul>
      <li class="member-list"
      v-for="item in memberList"
      :key="item.member"
      :class="{'active': item.member === chooseMember}"
      :style="[{backgroundImage: `url(${item.bg})`},
      {zIndex: members.length-item.no}]">
        <a href="#"
        @click.prevent="clickMemberList(item.member)">
          <img class="icon" :src="item.icon" alt="">
          <div class="member-block">
            <h2>{{ item.member }}</h2>
            <h4>{{ item.detail }}</h4>
          </div>
          <div class="price-block">
            <h3>{{ item.price }}</h3>
            <button
            v-if="chooseMember===item.member"
            @click="clickAdd(item)"
            >立即加入</button>
          </div>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Home',
  props: {
    newMember: {
      type: Object,
      default: function() {
        return {
          no: 1,
          member: '普通会员',
          detail: '每日可领取3次任务',
          price: '￥10.00',
          bg: require(`../assets/img/會員底圖-04.jpg`),
          icon: require('../assets/img/蒙版组 47.svg'),
        }
      }
    }
  },
  data() {
    return {
      members: [
        {
          no: 1,
          member: '普通会员',
          detail: '每日可领取3次任务',
          price: '￥10.00',
          bg: require(`../assets/img/會員底圖-04.jpg`),
          icon: require('../assets/img/蒙版组 47.svg'),
        },
        {
          no: 2,
          member: '白银会员',
          detail: '每日可领取10次任务 [1.20元/条]',
          price: '￥330.00',
          bg: require(`../assets/img/會員底圖-06.jpg`),
          icon: require('../assets/img/蒙版组 47.svg'),
        },
        {
          no: 3,
          member: '黄金会员',
          detail: '每日可领取19次任务',
          price: '￥660.00',
          bg: require(`../assets/img/會員底圖-02.jpg`),
          icon: require('../assets/img/蒙版组 36.svg'),
        },
        {
          no: 4,
          member: '铂金会员',
          detail: '每日可领取28次任务',
          price: '￥990.00',
          bg: require(`../assets/img/會員底圖-03.jpg`),
          icon: require('../assets/img/蒙版组 42.svg'),
        },
        {
          no: 5,
          member: '钻石会员',
          detail: '每日可领取99次任务',
          price: '￥2990.00',
          bg: require(`../assets/img/會員底圖-01.jpg`),
          icon: require('../assets/img/蒙版组 33.svg'),
        },
        {
          no: 6,
          member: '荣耀会员',
          detail: '每日可领取228次任务',
          price: '￥5940.00',
          bg: require(`../assets/img/會員底圖-05.jpg`),
          icon: require('../assets/img/蒙版组 40.svg'),
        },
        {
          no: 7,
          member: '尊耀会员',
          detail: '每日可领取338次任务',
          price: '￥2990.00',
          bg: require(`../assets/img/會員底圖-07.jpg`),
          icon: require('../assets/img/蒙版组 44.svg'),
        },
      ],
      nowMember: {},
      memberList: [],
      chooseMember: '',
    }
  },
  methods: {
    updateList() {
      this.memberList = [];
      this.members.forEach(item => {
        if(item.member !== this.nowMember.member) {
          this.memberList.push(Object.assign({}, item));
        }  
      });
    },
    clickMemberList(member) {
      this.updateList();
      this.chooseMember = member;
    },
    clickAdd(item) {
      this.$emit('openAlert', item)
    }
  },
  watch: {
    newMember() {
      this.nowMember = this.newMember;
      this.updateList();
    }
  },
  mounted() {
    this.nowMember = this.members[0];
    this.updateList();
  }
}
</script>

