<template>

  <section>
    <div class="restaurants u-flex u-flex-fd--c mlr-xxl">
    <div class="restaurants__user  fs-lg pb-lg u-flex u-flex-fd--r">
      <div class="first__left">User, odaberite željeni restoran</div>
      <div class="first__right u-flex u-flex-jc-fe">
        
         <nuxt-link to="/history/"> <button class="btn order btn_last"> <span class="icon-new-history"></span>Prošle narudžbe</button></nuxt-link>
         
      </div>
      
    </div>

    <h1 class="fs xxl loader" v-if="isLoading"></h1>
     
    

    <div class="restaurants__list u-flex  u-flex-jc--sb u-flex-fw--w" v-else>
      <SingleRestaurant v-for="restaurant in restaurants" :key="restaurant.id" :restaurantInfo="restaurant" />
    </div>
    
    </div>

    <!-- <div class="footer">
      
        <BottomNavToggle @toggle="$emit('bottomNavToggle')" />

      
          <div class="footer-components  u-flex u-flex-jc--c mlr-xxl mt-sm ">
        <div class="footer-components__center ptb-xs">
            <p>Aktivne narudžbe (2)</p>
        </div>
        
    </div>
      
    </div> -->
    <!-- proba -->
    

    <div class="footer">
    <div class="footer-components  u-flex u-flex-jc--c u-flex-ai--c mlr-xxl mt-sm ">
        
        <div class="footer-components__center ptb-xs">
            <p @click="openFooter">Aktivne narudžbe (2)</p>
           
        </div>
      
    </div>
    <collapse-transition>
			<div v-show="showFooter">
                <div class="hiddenOrders u-flex u-flex-fd--c u-flex-jc--c u-flex-ai--c ">
                <div class=" hiddenOtrders__singleRestaurant u-flex u-flex-fd--r u-flex-jc--sb">
                    <div class="hiddenOtrders-singleRestaurant__restaurantTime u-flex u-flex-fd--r pl-xs ">
                        <p class="hiddenOtrders-singleRestaurant-restaurantTime__title font-normal-bold fs-md pt-xs">Fast Food Forever</p>
                        <p  class="hiddenOtrders-singleRestaurant-restaurantTime__paragraf pt-xs ">(otvorio - User 09:42)</p>
                    </div>
                    <div class="hiddenOtrders-singleRestaurant__join ">
                        <button class="btn btn-join ptb-xs ">Pridruži se</button>
                    </div>
                </div>

                
                

                </div>
				
			</div>
		</collapse-transition>

 


      
    </div>
    
  </section>
</template>
<script>
import SingleRestaurant from '@/components/SingleRestaurant'
import BottomNavToggle from "@/components/BottomNavToggle";
import { CollapseTransition } from 'vue2-transitions';
export default {

  data(){
    return{
      restaurants:[],
      isLoading:true,
       showFooter: false
    }
  },
  components: {
    SingleRestaurant,
    BottomNavToggle,
    CollapseTransition 
  },
  created(){
    this.$axios.get(process.env.baseApiUrl + 'restaurants').then(res =>{
      this.restaurants= res.data.data
      this.isLoading=false
    
    })


  },
  methods:{
        openFooter(){
            console.log(this.showFooter)
            this.showFooter = !this.showFooter
        }
    }

 
}
</script>

<style scoped lang="scss">
    .restaurants{
        position: relative;
    padding-top: 180px;
    // margin: 0 auto;
    // width: 1440px;
    
    }

    .restaurants__user{
        // padding-right: 240px;
            //  font-size: 40px;
    line-height: 48px;
    font-style: bold;
    font-weight: bold;
    font-style: normal;
    letter-spacing: -0.5px;
    // padding-bottom: 80px;
    }

    // .first__left{
    //         font-size: 40px;
    // line-height: 48px;
    // font-style: bold;
    // font-weight: bold;
    // font-style: normal;
    // letter-spacing: -0.5px;
    // padding-bottom: 80px;
    // }

    .restaurants__list{
      padding-bottom: 96px;
    }
    .btn_last{
      margin-left:54%;
    }

     button.btn.order{
     position: absolute;
    border: 1px solid #070707;
    box-sizing: border-box;
    background: $tertiary-color;
    width: 220px;
    height: 44px;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 24px;
    letter-spacing: 0.1px;
    
} 
/* spiner */
.loader {
  border: 16px solid #f3f3f3;
  border-radius: 50%;
  border-top: 16px solid gray;
  width: 100px;
  height: 100px;
  -webkit-animation: spin 2s linear infinite; /* Safari */
  animation: spin 2s linear infinite;
}

/* Safari */
@-webkit-keyframes spin {
  0% { -webkit-transform: rotate(0deg); }
  100% { -webkit-transform: rotate(360deg); }
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.footer{
  box-sizing: border-box;
  border: 1px solid $primary-color;
  background-color: $primary-color;
  bottom:0px;
  height:100px;
}

.footer-components__center{
    color: $tertiary-color;
} 

@media screen and (max-width: 1504px){

  .second{
        display: flex;
     /* flex-direction: column;  */
     flex-wrap: wrap;
    
    justify-content: center;
    align-items: center;
    width: 100%;
    margin-left: 100px;
    margin-right: 100px;

  }

  article{
    width:50%
  }
  .first{
    margin-left:100px;
  }
}

//fotter

.hiddenOrders{
    width:100%;
    background-color:black;
    padding: 10px 10%;
    
}

.hiddenOtrders__singleRestaurant{
    width:100%;
    padding:30px;
    background-color:white;
    margin-top:2px;
}

.hiddenOtrders-singleRestaurant__join{
    background-color: $secondary-color;
}

.btn-join{
    padding-left: 16px;
    padding-right:16px;
}

</style>
