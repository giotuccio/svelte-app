<script>
  import CardWrapper from "./CardWrapper.svelte"
  import { cart } from "./stores.js";
    import { Router, Route, Link } from "svelte-navigator";
  
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    let cart_sum = 0;
    const unsubscribe = cart.subscribe(items => {
      const itemValues = Object.values(items);
      cart_sum = 0;
      itemValues.forEach(item => {
        cart_sum += item.count;
      });
    });
    function goToHome() {
      dispatch("nav", {
        option: "home"
      });
    }
    function goToCheckout() {
      dispatch("nav", {
        option: "checkout"
      });
    }
</script>
<div data-aos="fade-right" class="container-fluid mainContainer">
    <!-- Navigation menu section -->
    <Router>
   <nav class="navbar navbar-expand-md navbar-dark">
      <a href="/"class="navbar-brand" >

     
  <!---->  <img class="logo" alt="" src="https://cdn.shopify.com/s/files/1/2675/0606/files/your-logo-here_480x480.png?v=1569285089"/>

      </a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#collapsibleNavbar">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="collapsibleNavbar">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link" href="#Store">STORE</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#Buy">SHOP</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#Sell">LOCATIONS</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#Contact">CONTACT</a>
          </li>
     
           <!-- svelte-ignore a11y-missing-attribute -->
           <li class="nav-item active"><Link to='checkout' class="nav-link" style="cursor:pointer;    margin: -16px 0px;" on:click={goToCheckout}>CART
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-cart-dash-fill" viewBox="0 0 16 16">
                    <path d="M.5 1a.5.5 0 0 0 0 1h1.11l.401 1.607 1.498 7.985A.5.5 0 0 0 4 12h1a2 2 0 1 0 0 4 2 2 0 0 0 0-4h7a2 2 0 1 0 0 4 2 2 0 0 0 0-4h1a.5.5 0 0 0 .491-.408l1.5-8A.5.5 0 0 0 14.5 3H2.89l-.405-1.621A.5.5 0 0 0 2 1H.5zM6 14a1 1 0 1 1-2 0 1 1 0 0 1 2 0zm7 0a1 1 0 1 1-2 0 1 1 0 0 1 2 0zM6.5 7h4a.5.5 0 0 1 0 1h-4a.5.5 0 0 1 0-1z"/>
                  </svg>
                </Link></li>
                <li class="nav-link active"> {#if cart_sum > 0} {cart_sum}
                  {/if} </li>
                    
                  </ul>
     <ul style="list-style: none;">
          <li class="nav-item">
                 <form action="" class="search-bar">
  <input type="search" name="search" pattern=".*\S.*" required>
  <button class="search-btn" type="submit">
    <span>Search</span>
  </button>
</form>
</li>
     </ul>
      


          
      </div>
    </nav>
    </Router>
    <!-- legend section   -->
    <div class="row legend">
      <!-- legend introduction text -->
      <div class="col legend__text">
        <header class="introText">
          <h1 class="introText__heading">
            <b style="color:#e99044;">Savor the holiday savings</b> <span style="color:white">DECK THE WHOLE HOUSE </span>
          </h1>

          <p class="introText__link">
            <a href="#Visit">Check out our collection
              <i class="fas fa-arrow-right    "></i></a>
          </p>
          <br/>
          <button class="btn button">SHOP NOW</button>
        </header>
      </div>
    </div>
    <!-- footer section  -->
  </div>
  <CardWrapper/>
  <style>
      @import url("https://fonts.googleapis.com/css2?family=Lato&display=swap");

input {
  color: #171717;
    font: 1em Hind, sans-serif;
  line-height: 1.5em;
}
 .search-bar {
  display: flex;
}

.search-bar input,
.search-btn, 
.search-btn:before, 
.search-btn:after {
  transition: all 0.25s ease-out;
}
.search-bar input,
.search-btn {
  width: 3em;
  height: 3em;
}
.search-bar input:invalid:not(:focus),
.search-btn {
  cursor: pointer;
}
.search-bar,
.search-bar input:focus,
.search-bar input:valid  {
  width: 100%;
}
.search-bar input:focus,
.search-bar input:not(:focus) + .search-btn:focus {
  outline: transparent;
}
.search-bar {
margin: -10px auto;  justify-content: center;
  max-width: 30em;
}
.search-bar input {
  background: transparent;
  border-radius: 1.5em;
  box-shadow: 0 0 0 0.4em black inset;
  padding: 0.75em;
  transform: translate(0.5em,0.5em) scale(0.5);
  transform-origin: 100% 0;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
.search-bar input::-webkit-search-decoration {
  -webkit-appearance: none;
}
.search-bar input:focus,
.search-bar input:valid {
  background: #fff;
  width:23em;
  border-radius: 0.375em 0 0 0.375em;
  box-shadow: 0 0 0 0.1em #d9d9d9 inset;
  transform: scale(1);
}
.search-btn {
  background: black;
  border-radius: 0 0.75em 0.75em 0 / 0 1.5em 1.5em 0;
  padding: 0.75em;
  position: relative;
  transform: translate(0.25em,0.25em) rotate(45deg) scale(0.25,0.125);
  transform-origin: 0 50%;
}
.search-btn:before, 
.search-btn:after {
  content: "";
  display: block;
  opacity: 0;
  position: absolute;
}
.search-btn:before {
  border-radius: 50%;
  box-shadow: 0 0 0 0.2em #f1f1f1 inset;
  top: 0.75em;
  left: 0.75em;
  width: 1.2em;
  height: 1.2em;
}
.search-btn:after {
  background: #f1f1f1;
  border-radius: 0 0.25em 0.25em 0;
  top: 51%;
  left: 51%;
  width: 0.75em;
  height: 0.25em;
  transform: translate(0.2em,0) rotate(45deg);
  transform-origin: 0 50%;
}
.search-btn span {
  display: inline-block;
  overflow: hidden;
  width: 1px;
  height: 1px;
}

/* Active state */
.search-bar input:focus + .search-btn,
.search-bar input:valid + .search-btn {
  background: #e99044;
  border-radius: 0 0.375em 0.375em 0;
  transform: scale(1);
}
.search-bar input:focus + .search-btn:before, 
.search-bar input:focus + .search-btn:after,
.search-bar input:valid + .search-btn:before, 
.search-bar input:valid + .search-btn:after {
  opacity: 1;
}
.search-bar input:focus + .search-btn:hover,
.search-bar input:valid + .search-btn:hover,
.search-bar input:valid:not(:focus) + .search-btn:focus {
  background: #e99044;
}
.search-bar input:focus + .search-btn:active,
.search-bar input:valid + .search-btn:active {
  transform: translateY(1px);
}

@media screen and (prefers-color-scheme: dark) {
input {
    color: #f1f1f1;
  }

  .search-bar input {
    box-shadow: 0 0 0 0.4em #f1f1f1 inset;
  }
  .search-bar input:focus,
  .search-bar input:valid {
    background: #3d3d3d;
    box-shadow: 0 0 0 0.1em #3d3d3d inset;
  }
  .search-btn {
    background: #f1f1f1;
  }
}
 * {
	 margin: 0;
	 padding: 0;
	 box-sizing: border-box;
}
/*Entire HTML body*/
.logo{
        height: 6vh;
}
.btn{
    height: 2em;
    color: #e99044;
    font-size: 26px;
    width: 17em;
    margin: 50px auto;
    border: 0.05em solid #e99044;
}
.btn:hover{
    background-color: #e99044;
    color:white;
}

  .mainContainer {
	 height: 900px !important;
	 padding: 0 8%;
	 background-image: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), url(https://res.cloudinary.com/goddy-game/image/upload/v1615409345/background_syp3re.png);
	 background-repeat: no-repeat;
	 background-size: 100% 100%;
	 overflow: hidden;
	/*Navigation menu section*/
	/*legend section*/
}
  .mainContainer .navbar {
	 height: 70px;
     display:inline-flex;
     width: 100%;
	 background-color: transparent;
	 padding: 0;
}
  .mainContainer .navbar .navbar-brand {
	 color: #fff;
	 font-weight: 800;
	 font-size: 24px;
	 line-height: 29px;
	 margin-left: 13%;
	 transition: all;
	 transition-duration: 1s;
}
  .mainContainer .navbar .navbar-brand:hover,  .mainContainer .navbar .navbar-brand:focus {
	 transform: scale(1.2);
	 -webkit-text-stroke: 1px #fff;
	 -webkit-text-stroke-color: transparent;
}
  .mainContainer .navbar .navbar-collapse {
	 justify-content: flex-end;
}
  .mainContainer .navbar .navbar-collapse .navbar-nav {
	 width: 55% !important;
	 position: relative;
       margin: 4px 0px -14px 0px;
}
  .mainContainer .navbar .navbar-collapse .navbar-nav .last {
	 position: absolute;
	 right: 0 !important;
}
  .mainContainer .navbar .navbar-collapse .navbar-nav .nav-item {
	 margin: 0 10px;
}
  .mainContainer .navbar .navbar-collapse .navbar-nav .nav-item .nav-link {
	 color: #fff;
	 padding: 10px 0x;
	 font-weight: 800;
	 transition: all;
	 transition-duration: 1s;
}
  .mainContainer .navbar .navbar-collapse .navbar-nav .nav-item .nav-link:hover, body .mainContainer .navbar .navbar-collapse .navbar-nav .nav-item .nav-link:active, body .mainContainer .navbar .navbar-collapse .navbar-nav .nav-item .nav-link:focus {
          color: #e99044;
text-decoration: underline ;
}
  .mainContainer .legend {
	 margin-top: 130px;
	 height: 770px;
	 color: #fff;
	/*legend introduction text*/
}
  .mainContainer .legend .legend__text {
	 width: 100%;
}
  .mainContainer .legend .legend__text .introText {
	 text-align: center;
         margin: 80px auto;

}
  .mainContainer .legend .legend__text .introText .introText__heading {
    font-size: 40px;
    line-height: 79px;
    margin-bottom: 47px;
    background: black;
    font-weight: 800;
    width: 100%;
        border: 5px double #e99044
}
  .mainContainer .legend .legend__text .introText .introText__heading span {
	 font-weight: 400;
}
  .mainContainer .legend .legend__text .introText .introText__link a {
	 color: #fff;
	 font-weight: 800;
          font-size:20px;

	 padding: 10px 0;
	 border-bottom: 2px solid #fff;
	 transition: all;
	 transition-duration: 1s;
}
  .mainContainer .legend .legend__text .introText .introText__link a:hover, body .mainContainer .legend .legend__text .introText .introText__link a:focus {
	 text-decoration: none;
	 filter: blur(1px);
}
.navbar-toggler{
    border: 2px solid black;
    background:#e99044;
}
.navbar-toggler-icon{
    color:black;
    font-size:16px;
}
/*Responsiveness for screens*/
 @media screen and (max-width: 1600px) {
	  .mainContainer .navbar .navbar-brand {
		 margin-left: 6%;
	}
}
 @media screen and (max-width: 1350px) {
	  .mainContainer .navbar .navbar-brand {
		 margin-left: 2%;
	}
}
 @media screen and (max-width: 1200px) {
	  .mainContainer {
		 padding: 0 3%;
	}
}
 @media screen and (max-width: 1000px) {
	  .mainContainer {
		 padding: 0 1%;
	}
	  .mainContainer .navbar .navbar-nav .last {
		 position: relative !important;
	}
}
 @media screen and (max-width: 767px) {
	.mainContainer {
		 padding: 0 2%;
		 height: 800px !important;
	}
 .mainContainer .navbar {
		 margin-bottom: 200px;
	}
.mainContainer .navbar .navbar-brand {
		 margin-left: 0 !important;
	}
.mainContainer .navbar .navbar-collapse .navbar-nav {
		 width: 100% !important;
		 background-color: #333;
	}
 .mainContainer .navbar .navbar-collapse .navbar-nav .last {
		 position: relative !important;
	}
.mainContainer .navbar .navbar-collapse .navbar-nav .nav-item .nav-link:hover, body .mainContainer .navbar .navbar-collapse .navbar-nav .nav-item .nav-link:active, body .mainContainer .navbar .navbar-collapse .navbar-nav .nav-item .nav-link:focus {
		 border-bottom: 2px solid #fff;
		 transform: translateY(-5px);
	}
	.mainContainer .legend {
		 height: 550px;
	}
	  .mainContainer .legend .legend__text {
		 padding: 0;
		 height: 400px !important;
	}
	  .mainContainer .legend .legend__text .introText {
		 width: 100%;
    margin: -95px 0px;
		 text-align: center;
	}
	  .mainContainer .legend .legend__text .introText .introText__heading {
		 font-size: 32px;
	}
}
 
  </style>

