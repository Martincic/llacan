<template>
    <section>
        <div class="menu-info u-flex u-flef-fd--r pt-sm">
        <div class="left__side">
        <div class="menu-info__left u-flex u-flex-fd--c">
            <div class="menu-info-left_inforestaurant">
                <div class="menu-info-left__img">
                    <img class="fast-food" src="~/assets/img/fast-food.png" />
                </div>
                    
                <div class="menu-info-left__info">
                    <h1 class="restaurant-title">{{restaurantInfo.title}}</h1>
        
                    <p class="restaurant-adress"><span class="icon-home-icon"></span>{{restaurantInfo.address}}</p>
                    <p class="restaurant-number"><span class="icon-phone-icon"></span>{{restaurantInfo.phone}}</p>

                </div>
                

               
                
                


            </div>
            
        </diV>
        <div class="categories">
            <div class="categories__title fs-md">
                <h1>Kategorije</h1>
            </div>
            <div class="categories__paragraf fs-base">
                <!-- <p class="single-categories">BURGER</p> -->
                 <!-- <p class="products"></p> -->
                      <!-- <nuxt-link :to="products.link" v-for="products in restaurantInfo.products" :key="products.category">{{category}}</nuxt-link> </p>   -->
                     <p>BURGER</p>
            </div >   

            <div class="categories__paragraf fs-base">
                <!-- <p class="single-categories">BURGER</p> -->
                 <!-- <p class="products"></p> -->
                      <!-- <nuxt-link :to="products.link" v-for="products in restaurantInfo.products" :key="products.category">{{category}}</nuxt-link> </p>   -->
                      <p>POMES</p>
            </div > 

               
            </div>    

             <div class="condements">
            <div class="condements__title fs-md">
                <h1>Dodaci</h1>
            </div>
            <div class="condements__paragraf fs-base">
                <p>kečap, ajvar, majoneza, kiseli krastavci</p>
                
            </div>

        </div>

        </div>

         <div class="menu-info__right u-flex u-flex-fd--r"  v-if="burgerProducts.length >0">
            <div class="menu-info-right__food">
                 <h1 class="title-restaurant border-box">Burger</h1> 
                  <!-- <h1 class="title-restaurant border-box">Burger</h1>  -->
              
             <div class="menu-info-right__food1  u-flex u-flex-fd-r u-flex-jc--sb" v-for="burger in burgerProducts" :key="burger.id">
                <div class="ingredients">
                    <!-- <p class="restaurant"></p> -->
                   <p class="title-food">{{burger.name}}</p>
                   
                     


                  
                <p class="ingredients-food">{{burger.description}}</p>
                </div>
                <div class="price fs-base">
                    
                      <p>{{burger.price}} kn</p>
                </div>
                
            </div> 
<!-- 
            <div v-if="burgerProducts.length >0">
                <h1>Burgers</h1>
                <div class="menu-info-right__food1" v-for="burger in burgerProducts" :key="burger.id">
                    <div class="ingredients">
                        <p class="title-food">{{burger.name}}</p>
                    <p class="ingredients-food">Juneća pljeskavica u pecivu, dodaci po želji</p>
                    </div>
                     <div class="price fs-base">
                    <p>{{burger.price}}</p>
                      
                </div>
                    
                </div>         
            </div> -->
            <!-- <div v-if="burgerProducts.length >0">
                <h1>Burgers</h1>
                <div class="menu-info-right__food1" v-for="burger in burgerProducts" :key="burger.id">
                    <div class="ingredients">
                        <p class="title-food">{{burger.name}}</p>
                    <p class="ingredients-food">Juneća pljeskavica u pecivu, dodaci po želji</p>
                    </div>
                    
                </div>         
            </div> -->

           
            
        </div>
</div>

       


        </div>
       
<div class="footer">
    <div class="footer-components  u-flex u-flex-jc--sb mlr-xxl mt-sm ">
        <div class="footer-components__left ptb-xs plr-xs">
           <nuxt-link to="/restaurants/">  <button class="btn btn-menu btn-button"><span class="icon-back-icon"></span>Natrag na restorane</button></nuxt-link>
             
        </div>
        <div class="footer-components__center ptb-xs">
            <p @click="openFooter">Aktivne narudžbe (2)</p>
            <!-- <div class="hiddenOrders u-flex u-flex-fd--c">
                <div class=" hiddenOtrders__singleRestaurant u-flex u-flex-fd--r">
                    <div class="hiddenOtrders-singleRestaurant__restaurantTime u-flex u-flex-fd--r pl-xs border-box">
                        <p>Fast Food Forever</p>
                        <p>(otvorio - User 09:42)</p>
                    </div>
                    <div class="hiddenOtrders-singleRestaurant__join">
                        <button class="btn btn-menu btn-button-new pr-xs ">Pridruži se</button>
                    </div>
                </div>
                

            </div> -->
        </div>
        <div class="footer-components__right ptb-xs plr-xs">
           <nuxt-link :to="`/restaurants/${restaurantInfo.slug}/order`" class="btn btn-menu btn-button-new">Nova narudžba</nuxt-link>
             
        </div>
        <!-- <div class="proba" style=" height:300px">
            <div>dfdsf</div>
            <div>sfds</div>

        </div> -->
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
import { CollapseTransition } from 'vue2-transitions';
export default {
   

     components:{
         CollapseTransition 
    },
    
    data(){
        return{
            restaurantInfo:'',
            isLoading:true,
            showFooter: false
        }
    },

    methods:{
        openFooter(){
            console.log(this.showFooter)
            this.showFooter = !this.showFooter
        }
    },

   created(){
    this.$axios.get(process.env.baseApiUrl + 'restaurants/' + this.$route.params.slug ).then(res =>{
      this.restaurantInfo= res.data.data
      this.isLoading=false
    
    })
  },
  computed:{
      burgerProducts(){
          if(!this.restaurantInfo) return []
          return this.restaurantInfo.products.filter(p => p.category === 'Burger')
      },
      paninProducts(){
          if(!this.restaurantInfo) return []
          return this.restaurantInfo.products.filter(p => p.category === 'Panin')
      }
  }
        
  
}
</script>

<style scoped lang="scss">

.menu-info{
    // padding-top:150px;
   position: relative;
    margin: 0 auto;
    width: 1440px;
    padding-bottom: 104px
}

.left__side{
    width: 33%;
}
.menu-info__left{
    border: 1px solid #EEEEEE;
    
    /* padding-left: 32px; */
}

.fast-food{
    width:100%;
}

.menu-info-left__info{
    padding-left: 32px;
    padding-bottom: 38.8px;
} 


.restaurant-title{
font-style: normal;
font-weight: bold;
font-size: 40px;
line-height: 48px;
letter-spacing: -0.5px;
}

.restaurant-adress{
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 24px;
    letter-spacing: 0.1px;
    padding-top: 16px;
}

.restaurant-number{
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 24px;
    letter-spacing: 0.1px;
    padding-top: 12px;
}

.menu-info-left__condements{
    border: 1px solid #EEEEEE;
    box-sizing:border-box;
   
}

.menu-info__right{
    width: 67%;
}

.menu-info__right{
    margin-left:24px;
}
.tag{
    padding-top:46px;
}

.tag2{
    padding-left:40px;
    
}

.categories, .condements{
    margin-top:30px;
    border: 1px solid #EEEEEE;
box-sizing: border-box;

}

.categories__title, .condements__title{
    border: 1px solid #EEEEEE;
box-sizing: border-box;
padding-bottom: 24px;
padding-top:24px;
padding-bottom: 24px;
padding-left:32px;
}

.categories__paragraf, .condements__paragraf{
    border: 1px solid #EEEEEE;
box-sizing: border-box;
padding-top: 24px;
    padding-bottom: 33px;
    padding-left: 32px;
}

.single-categories{
    padding-bottom: 20px;
}




/* RIGHT */
.title-restaurant{
    font-style: normal;
font-weight: bold;
font-size: 32px;
line-height: 38px;
letter-spacing: -0.4px;
width: 952px;
height: 100px;
}

.menu-info__right{
    background: $tertiary-color;
/* Backgrounds / Light Gray */

// border: 1px solid #EEEEEE;
// box-sizing: border-box;
//  width: 80%;
}

.menu-info-right__food1{
    background: $tertiary-color;
/* Backgrounds / Light Gray */

    
   
  

border: 1px solid #EEEEEE;
box-sizing: border-box;
}

.ingredients{
    padding-top: 11px;
    padding-bottom: 10.5px;
    padding-left: 49px;
}

.title-restaurant{
    padding-top: 31px;
    padding-left: 47px;
}

.title-food{
    font-style: normal;
    font-weight: 500;
    font-size: 18px;
    line-height: 28px;
    color: #070707;
   
}

.ingredients-food{
    font-style: normal;
font-weight: normal;
font-size: 14px;
line-height: 20px;
color: #070707;

}

.price{
    padding-top: 24.6px;
   
    padding-bottom: 24.9px;
    padding-right: 40px;
}
// .footer{
//   box-sizing: border-box;
//   border: 1px solid $primary-color;
//   background-color: $primary-color;
//   bottom:0px;
//   height:100px;
// }

// .footer-components__left{
//     background-color: $tertiary-color;
// }
// .footer-components__center{
//     color: $tertiary-color;
// } 
// .footer-components__right{
//      background-color: $secondary-color;
// }

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