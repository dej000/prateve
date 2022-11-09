<template>
    <header class="header d-flex justify-content-between  align-items-center " :class="{'scrolled-nav':scrolledNav}"> 
         
       <a class="logo text-decoration-none" href=""><img src="https://res.cloudinary.com/di6dtlbpj/image/upload/v1667942079/image_1_w7ipbp.svg" alt=""></a>
       
        <nav class="navbar d-flex">
            <ul v-show="!mobile" class="navigation">
                <li><a href="#home">Home</a></li>
               
                <li> <a class="  dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                    Company
                   </a></li>   
                  
                    <!-- <ul class="dropdown-menu">
                      <li><a class="dropdown-item" href="#">Action</a></li>
                      <li><a class="dropdown-item" href="#">Another action</a></li>
                      <li><a class="dropdown-item" href="#">Something else here</a></li>
                    </ul> -->
                 
                <li><a href="#">FAQS</a></li>
            
            </ul>    
        </nav>
       <div  v-show="!mobile">
        <button type="button" class="btn btn-primary">get started  <i class="fa fa-arrow-right" aria-hidden="true"></i></button>
       </div>
        
       <div class="icon">
        <i @click="toggleMobileNav" v-show="mobile" class="far fa-bars " style="color:rgba(30, 129, 196, 1)" :class="{'icon-active':mobileNav}"></i>
       </div>

       <transition>
        <ul v-show="mobileNav" class="dropdown-nav ">
            <li @click="toggleMobileNav"><a href="#">HOME</a></li>
            
            <li @click="toggleMobileNav"><a href="#">FAQS</a></li> 
        
        </ul>   
       </transition>
        
    </header>

</template>

<script>
    export default {
        name :'navigation',
        data(){
            return{
                scrolledNav:null,
                mobile:null,
                mobileNav:null,
                windowWidth:null,
            }
        },
        created(){
            window.addEventListener('resize',this.checkScreen)
            this.checkScreen()
        },

        mounted(){
            window.addEventListener('scroll',this.updateScroll)
        },
        methods: {
            toggleMobileNav(){
                this.mobileNav =!this.mobileNav
            },

            updateScroll() {
                const scrollPosition = window.scrollY;
                if(scrollPosition > 460){
                    this.scrolledNav = true;
                    return
                }
                this.scrolledNav = false
            },

            checkScreen(){
                this.windowWidth =window.innerWidth;
                if(this.windowWidth <= 750){
                    this.mobile = true
                    return
                }
                this.mobile = false;
                this.mobileNav = false;
                return;
            }
        },
    }
</script>

<style  scoped>

.header{
    padding: 0px 10%;
    z-index: 999;
    transition: .5s ease all;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    right: 0;
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.15);
    backdrop-filter: blur(5px);
    background-color: rgba(255, 255, 255);
    font-family: 'poppins';
    
}




.btn{
    background: linear-gradient(270deg, #1E81C4 0%, #0F4062 100%);
    padding: 10px;
    width: 120px;
}

.scrolled-nav{
    background-color: rgb(141, 132, 132,0);
    box-shadow: 0 20px 50px rgb(0 0 0 / 46%);
    backdrop-filter: blur(5px);
    height: 50px;
    transition: .3s ease;
}

.scrolled-nav header{
    padding: 3px 10%;
}

.scrolled-nav .logo img{
    height: 30px;

}

.scrolled-nav .navbar a{
    font-size: 12px;
    color: rgb(255, 255, 255);
}


.icon{
    color: white;
    cursor: pointer;
   
}

.icon i{
    transition: 0.8s ease all;
}

.icon-active{
    transform: rotate(180deg);
}

.dropdown-nav{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: fixed;
    width: 50%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.75);
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(1.7857142857rem);
    top: 45px;
    right: 0;
    gap: 20px;
    transition: height .2s ease-in-out;
    padding: 0;
    

   
    
} 

.dropdown-nav::before{
    content: '';
   position: absolute;
   width: 100%;
   height: 100%;
   background-color: rgba(16, 16, 16, 0.5);
   backdrop-filter: blur(1.7857142857rem);
   z-index: -1;
}

.dropdown-nav li{
     margin-left: 0;
     list-style: none;
     
}

.dropdown-nav a{
    color: white;
    text-decoration: none;
    padding: 5px;
}

.dropdown-nav a:hover{
    color: whitesmoke;
    box-shadow: inset 100px 0 0 0 #636768;

}





.navigation{
    display: flex;
    align-items: center;
    flex: 1;
    justify-content: center;
}

.navigation li{
    list-style: none;
    margin-left: 60px;
    display: flex;
    
}

ul.navigation{
    margin-bottom: 0;
    padding-left: 0;
}


nav.navbar a{
    box-shadow: inset 0 0 0 0 #4e5051;
    color: rgb(3, 3, 3); 
    padding: 4px;
    font-size: 14px;
    transition: color .3s ease-in-out, box-shadow .3s ease-in-out ;
    text-decoration: none;
}



li a:hover {
    color: #0087ca;
    display: inline-block;
    position: relative;
 

}  


 

@media (max-width : 750px){
    .header .nav-links{
        display: none ;
     }
    
     .header .nav-links.active{
        position: fixed;
        height: 100vh;
        width: 100%;
        top: 0;
        left: 0;
        display: flex;
        flex-direction: column ;
        justify-content: center;
        align-items: center;
        background: rgba(1,1,1,0.9);
     }
      
  
    
    
     header nav.navbar a{
        box-shadow: inset 0 0 0 0 #54b3d6;
        color: rgb(255, 255, 255);
        font-weight:bold;
        padding: 4px;
        font-size: 14px;
        transition: color .3s ease-in-out, box-shadow .3s ease-in-out ;
        
    }
    
    
}

</style>