<template>
  <div class="base-info" v-if="Object.keys(goods).length !==0">
      <div class="info-title">{{goods.title}}</div>
      <div class="info-price">
        <span class="n-price">{{goods.newPrice}}</span>
        <span class="o-price">{{goods.oldPrice}}</span>
        <span class="discount" v-if="goods.discount">{{goods.discount}}</span>
      </div>
      <div class="info-other">
        <span>{{goods.columns[0]}}</span>
        <span>{{goods.columns[1]}}</span>
        <span>{{goods.services[goods.services.length-1].name}}</span>
      </div>
      <div class="info-service">
        <span class="info-service-item" v-for="index in goods.services.length-1" :key="index">
          <img :src="goods.services[index-1].icon">
          <span>{{goods.services[index-1].name}}</span>
        </span>
    </div>
  </div>
</template>

<script>
export default {
    name:'DetailBaseInfo',
    props:{
      goods:{
        type:Object,
        default(){
          return {} 
        }
      }
    }
}
</script>

<style>
.base-info{
  margin-top: 15px;
  padding: 0 8px;
  color: #999;
  border-bottom: 5px solid #f2f5f8;
}
.info-title{
  color: #222;
}
.info-price{
  margin-top: 10px;
}
.info-price .n-price{
  color: var(--color-high-text);
  font-size: 20px;
  margin-right: 8px;
}
.info-price .o-price{
  text-decoration: line-through;
  margin-right: 8px;
}
.info-price .discount{
  background-color: var(--color-high-text);
  border-radius: 5px;
  color: #fff;
  padding: 2px 5px;
}
.info-other{
  display: flex;
  justify-content: space-between;
  line-height: 60px;
}
.info-service{
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
}
.info-service-item img{
  width: 14px;
  height: 14px;
  position: relative;
  top: 2px;
}
.info-service-item span{
  font-size: 13px;
  color: #333;
}
</style>