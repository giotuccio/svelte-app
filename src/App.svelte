<script>
  import Landing from "./Landing.svelte";
  import { Route, Router } from "svelte-navigator";
  import ImageGrid from "./ImageGrid.svelte";
  import Routes from "./Routes.svelte";
  import Navigation from "./Navigation.svelte";
  import Carousel from "./Carousel.svelte";
  import Footer from "./Footer.svelte";
  import Chatbox from "./Chatbox.svelte";
  import AddCart from "./AddCart.svelte";
  import Checkout from "./Checkout.svelte";
  function HandleClick(e) {
    console.log(e.detail.src);
  }
  AOS.init();
</script>
<Landing/>
<Router>

  <Route path="checkout">
    <Checkout />
  </Route>
  </Router
>
<hr/>
<Navigation />

<hr />
<ImageGrid gap={15} maxColumnWidth={250} on:click={HandleClick}>
  <img
    class="banner-imgs"
    src="https://ashleyfurniture.scene7.com/is/image/AshleyFurniture/2440238-10X8-CROP?$AFHS-PDP-Main$"
    alt=""
  />

  <img
    class="banner-imgs"
    src="https://ashleyfurniture.scene7.com/is/image/AshleyFurniture/2440238-10X8-CROP?$AFHS-PDP-Main$"
    alt=""
  />
  <img
    class="banner-imgs"
    src="https://ashleyfurniture.scene7.com/is/image/AshleyFurniture/2440238-10X8-CROP?$AFHS-PDP-Main$"
    alt=""
  />
  <img
    class="banner-imgs"
    src="https://ashleyfurniture.scene7.com/is/image/AshleyFurniture/2440238-10X8-CROP?$AFHS-PDP-Main$"
    alt=""
  />
  <img
    class="banner-imgs"
    src="https://ashleyfurniture.scene7.com/is/image/AshleyFurniture/2440238-10X8-CROP?$AFHS-PDP-Main$"
    alt=""
  />
  <img
    class="banner-imgs"
    src="https://ashleyfurniture.scene7.com/is/image/AshleyFurniture/2440238-10X8-CROP?$AFHS-PDP-Main$"
    alt=""
  />
</ImageGrid>
<br />

<hr />
<Routes style="background-color:#e99044" />
<br /><br />
<br />

<hr />

<Carousel />
<hr />
<Chatbox />
<Footer />

<!-- svelte-ignore missing-declaration -->
<style>
</style>
