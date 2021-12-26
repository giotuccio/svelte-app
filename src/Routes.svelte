<script>
  let products = [
    {
      id: 1,
      name: "Apple",
      image: "/path/to/apple.png",
      price: 10,
      quantity: 1,
    },
    
  ];

  export let cart = [];
  export function  addToCart(product) {
    for (let item of cart) {
      if (item.id === product.id) {
        product.quantity += 1;
        cart = cart;
        return;
      }
    }
  cart = [...cart, product];
  };
  $: total = cart.reduce((sum, item) => sum + item.quantity, 0);
  export let total;
  
</script>

<div class="container">
  <h2 class="title">See our holiday discounts!</h2>
  <div class="row blogs">
    <div class="col-md">
      <div class="card mb-3">
        <a href="http://localhost:59560/"
          ><img
            src="https://ashleyfurniture.scene7.com/is/image/AshleyFurniture/77005-58-46-62?$AFHS-Grid-1X$"
            class="card-img-top"
            alt="..."
          /></a
        >

        <div class="card-body">
          <h5 class="card-title">Power</h5>
          <p class="card-text">
            SvelteKit is an application framework powered by Svelte — build
            bigger apps with a smaller footprint and no headaches
          </p>
          <a href="https://svelte.dev/" class="btn btn-primary">VIEW</a>
          <br />
          <br />
          {#each products as product}
            <input type="button" class="btn" on:click={() => addToCart(product)}  value="ADD TO CART" />
            <input style="width: 22px;"type="text" bind:value={total} readonly />

          {/each}
         

        </div>
      </div>
    </div>
    <div class="col-md">
      <div class="card mb-3">
        <a href="http://localhost:59560/"
          ><img
            src="https://ashleyfurniture.scene7.com/is/image/AshleyFurniture/77005-58-46-62?$AFHS-Grid-1X$"
            class="card-img-top"
            alt="..."
          /></a
        >

        <div class="card-body">
          <h5 class="card-title">Sveltekit</h5>
          <p class="card-text">
            A framework for building web applications, with a simple development
            experience and flexible filesystem-based routing
          </p>
          <a href="https://kit.svelte.dev" class="btn btn-primary">VIEW</a>
          <br />
          <br />
          {#each products as product}
              <input type="button" class="btn" on:click={() => addToCart(product)}  value="ADD TO CART" />
            <input style="width: 22px;"type="text" bind:value={total} readonly />
          {/each}
        </div>
      </div>
    </div>
    <div class="col-md">
      <div class="card mb-3">
        <a href="http://localhost:59560/"
          ><img
            src="https://ashleyfurniture.scene7.com/is/image/AshleyFurniture/77005-58-46-62?$AFHS-Grid-1X$"
            class="card-img-top"
            alt="..."
          /></a
        >
        <div class="card-body">
          <h5 class="card-title">Build fast</h5>
          <p class="card-text">
            Hit the ground running with advanced routing, server-side rendering,
            code-splitting, offline support and more
          </p>
          <a href="https://kit.svelte.dev/docs" class="btn btn-primary">VIEW</a>
          <br />
          <br />
          {#each products as product}
      <input type="button" class="btn" on:click={() => addToCart(product)}  value="ADD TO CART" />
            <input style="width: 22px;"type="text" bind:value={total} readonly />
          {/each}
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .card {
    border-radius: 7.35em;
  }
  .card-img-top {
    border-top-left-radius: calc(7.25rem - 1px);
    border-top-right-radius: calc(7.25rem - 1px);
  }
  .btn {
    color: #e99044;
    background: transparent;
    border: 1px solid #e99044;
    transition: ease-in-out 0.2s;
  }
  .btn:hover {
    background-color: #e99044;
    color: white;
  }
  .container {
    background: #e99044;
    display: grid;
    max-width: 100%;
    width: 100%;
    height: 900px;
    justify-content: space-around;
    align-content: stretch;
    justify-items: stretch;
    align-items: stretch;
  }
  .title {
    text-align: center;
    margin: 24px 0px;
  }
  .blogs {
    padding: 12px 12px 10px 12px;
    display: inline-flex;
    margin-top: 20px;
    text-align: center;
  }
  @media (max-width: 640px) {
    .col-md {
      width: 50%;
    }
  }
  @media (min-width: 640px) {
    .col-md {
      width: 50%;
    }
  }
</style>
