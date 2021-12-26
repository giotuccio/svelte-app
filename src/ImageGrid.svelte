<script>
    import { onMount, createEventDispatcher } from 'svelte';
    import { tick } from 'svelte';
    export let gap = 12;
    export let maxColumnWidth = 250;
	const dispatch = createEventDispatcher();
    let slotHolder = null;
    let columns = [];
    let galleryWidth = 0;
    let columnCount = 0;
    $: columnCount = parseInt(galleryWidth / maxColumnWidth) || 1;
    $: columnCount && Draw();
    $: galleryStyle = ` --gap: ${gap}px`;
    onMount(Draw);
    function HandleClick (e) {
        dispatch('click', { src: e.target.src });
	}
    async function Draw() {
        await tick();
        if (!slotHolder) { return }
        const images = Array.from(slotHolder.childNodes).filter(child => child.tagName === "IMG");
        columns = [];
        // Fill the columns with image URLs
        for (let i=0; i<images.length; i++) {
            const idx = i % columnCount;
            columns[idx] = [...columns[idx] || [], images[i].src];
        }
    }
      AOS.init();

</script>

<div data-aos="fade-right" id="slotHolder" bind:this={slotHolder} on:DOMNodeInserted={Draw} on:DOMNodeRemoved={Draw}>
    <slot></slot>
</div>
    <h2 data-aos="fade-right" class="title">Just In</h2>

{#if columns}
<div  data-aos="fade-right" id="gallery" bind:clientWidth={galleryWidth} style={galleryStyle}>
    {#each columns as column}
    <div class="column">
        {#each column as url}
       <a href="http://localhost:59560/"> <img src={url} alt="" on:click={HandleClick}/></a>
        {/each}
    </div>
    {/each}
</div>
{/if}
	<button class="shop-btn" style="cursor:pointer;">VIEW ALL</button>

<style>
    .title{
  text-align: center;
    margin: 53px 0px;
}
.shop-btn{
      height: 3em;
    color: #e99044;
    font-size: 21px;
    width: 17em;
    display: block;
    background-color: transparent;
    margin: 33px auto;
    transition: ease-in-out .2s;
        border: 0.05em solid #e99044;
}
.shop-btn:hover{
     background-color: #e99044;
    color:white;
}
    #slotHolder { display: none }
    #gallery { width: 100%; display: grid; gap: var(--gap);grid-template-columns: repeat(6, 1fr); }
    #gallery .column { display: flex; flex-direction: column }
    #gallery .column * { width: 100%; margin-top: var(--gap) }
    #gallery .column *:nth-child(1) { margin-top: 0;    height: 38vh; }
	@media (max-width: 640px) {
	    #gallery { width: 100%; display: grid; gap: var(--gap);grid-template-columns: repeat(1, 1fr); }

	}
     	@media (min-width: 640px) and (max-width:900px) {
	    #gallery { width: 100%; display: grid; gap: var(--gap);grid-template-columns: repeat(2, 1fr); }

	}
@media only screen and (min-width: 810px) and (max-width: 1080px)  { 	    #gallery { width: 100%; display: grid; gap: var(--gap);grid-template-columns: repeat(3, 1fr); }
 }
</style>