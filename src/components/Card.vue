<script>

export default {
    props: {
        item: {
            type: Object,
            required: true
        }
    },
    methods: {
        onClick() {
            this.$emit('show')
        }
    }
}
</script>

<template>
    <div class="col-4">
        <figure class="img-container">
            <img class="img" :src="'/img/' + item.frontImage" alt="">
            <img class="img-back" :src="'/img/' + item.backImage" alt="">
        </figure>
        <div class="info-product">
            <h3 class="mark">{{ item.brand }}</h3>
            <p @click="$emit('show', item)" class="product-description">{{ item.name }}</p>
            <div>
                <!-- <span class="sale">14,99 &euro; </span> -->
                <span>{{ item.price }} &euro;</span>
                <div class="heart">&#x2665;</div>
                <div class="badge">
                    <div :class="{ 'bg-red': badge.type === 'discount', 'bg-green': badge.value === 'Sostenibilità' }"
                        v-for="(badge, i) in item.badges" :key="i">{{
                            badge.value }}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped> .mark {
     font-size: 17px;
 }

 .info-product {
     display: flex;
     flex-direction: column;
     align-items: flex-start;
 }

 .barred {
     text-decoration: line-through;
     font-size: 13px;
 }

 .sale {
     color: red;
     font-size: 13px;
 }

 .product-description {
     text-transform: uppercase;
     font-weight: 600;
 }

 .heart {
     background-color: white;
     width: 30px;
     aspect-ratio: 1;
     display: flex;
     justify-content: center;
     align-items: center;
     font-size: 15px;
     position: absolute;
     top: 40px;
     right: 10px;
 }

 .bg-red {
     background-color: red;
     color: white;
     font-weight: 600;
     padding: 5px;
 }

 .bg-green {
     background-color: green;
     color: white;
     font-weight: 600;
     padding: 5px;
 }

 .badge {
     display: flex;
     gap: 5px;
     position: absolute;
     bottom: 110px;
     font-size: 13px;
 }

 .img {
    position: relative;
 }

.img-back {
    position: absolute;
    opacity: 0;
    padding: 5px;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
 

 .img:hover {
     opacity: 0;
 }

 .img-back:hover {
    opacity: 1;
 }


</style>