<script>
  import { onMount } from 'svelte';

  import Header from "./components/Header.svelte"
  import Post from "./components/Post.svelte"
  import News from "./components/News.svelte"
  import Features from "./components/Features.svelte"
  
  let data;
  let components = [];
  let item = false;
  let index;
  let user = false;

  onMount(async function() {
    const response = await fetch(cfg.dataPath);
    data = await response.json();
    
    console.log(components)
    window.components = components;
    window.data = data;
    
     
    let root = document.documentElement;
    root.style.setProperty('--bg-color', data.design.color1);
    root.style.setProperty('--fg-color', data.design.color2);
    root.style.setProperty('--font', data.design.font);
  })
  
  // this function receives updates from the cms
  window.relay = function(mydata) {
    // console.log(data);
    data = mydata;
  }
 
</script>

<div id="content">
{#if data}
  {#each data.items as item, i}

  {#if item.component == 'Header'}
  <Header bind:item bind:components />		
  {/if}
  {#if item.component == 'Post'}
  <Post bind:item bind:components />
  {/if}
  {#if item.component == 'News'}
  <News bind:item bind:components />
  {/if}
  {#if item.component == 'Features'}
  <Features bind:item bind:components />
  {/if}
  

  {/each}
{/if}  
</div>
  
<!-- We need to include them at least once -->
<Header bind:item bind:components />	
<Post bind:item bind:components /> 
<News bind:item bind:components />
<Features bind:item bind:components />




