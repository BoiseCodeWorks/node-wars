<template>
  <div class="hello">
    <div v-for="target in targets">
      <img :src="target.imgUrl">
      <h1 :class="{
        healthy: target.health > 90,
        warning: target.health < 90 && target.health > 50,
        'near-death': target.health < 50 && target.health> 0,
        dead: target.health == 0
      }">{{ target.health ? target.health : target.name + ' has fainted' }}</h1>
      <div>
        <button v-for="(damage, attackType) in target.attackTypes" @click="attack(attackType, target)" :disabled="target.health < damage">
          {{attackType}}
        </button>
        <!-- <button @click="attack('slap', target)" :disabled="target.health <= 0">slap</button>
        <button @click="attack('punch', target)" :disabled="target.health <= 4">punch</button>
        <button @click="attack('kick', target)" :disabled="target.health <= 9">kick</button> -->
        <button @click="reset(target)">reset</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        targets: [{
          name: 'Po',
          health: 100,
          imgs:{
            start:'https://vignette.wikia.nocookie.net/kungfupanda/images/7/73/KFP3-promo-po4.jpg/revision/latest/scale-to-width-down/350?cb=20150726165358',
            hurt: 'https://i.ytimg.com/vi/c_jUb-Gz4uo/maxresdefault.jpg' 
          },
          imgUrl: 'https://vignette.wikia.nocookie.net/kungfupanda/images/7/73/KFP3-promo-po4.jpg/revision/latest/scale-to-width-down/350?cb=20150726165358',
          attackTypes: {
            slap: 1,
            punch: 5,
            kick: 10
          }
        }, {
          name: 'Shifu',
          health: 150,
          imgs:{
            start:'https://vignette.wikia.nocookie.net/vsbattles/images/5/5a/Shifu_action.png/revision/latest?cb=20170202095824',
            hurt: 'https://img00.deviantart.net/6348/i/2015/049/c/e/master_shifu_by_fabylp-d8ijh0u.jpg' 
          },
          imgUrl: 'https://vignette.wikia.nocookie.net/vsbattles/images/5/5a/Shifu_action.png/revision/latest?cb=20170202095824',
          attackTypes: {
            slap: 5,
            punch: 0,
            kick: 8
          }
        }]
      }
    },
    methods: {
      attack(attackType, target) {
        var damage = target.attackTypes[attackType]
        if (damage) {
          target.health -= damage
          if (target.health <= 50) {
            target.imgUrl = target.imgs.hurt
          }
        }
      },
      reset(target) {
        target.health = 100
        target.imgUrl = target.imgs.start
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .healthy {
    color: green;
  }

  .warning {
    color: orange;
  }

  .near-death {
    color: orangered;
  }

  .dead {
    color: rgba(100, 100, 100, .3);
  }

  img{
    height: 55px
  }
</style>