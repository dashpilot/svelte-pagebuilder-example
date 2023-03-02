<script>
export let item;
export let components;
if(!item){
components.push({
			"component": "Header",
			"name": "Header",
			"fields": {
			  "icon": "icn",
			  "title":"txt",
			  "subtitle": "txt",
			  "button_text": "txt",
			  "button_link": "txt"
		  }
	  })
}
</script>

{#if item}
<section>
	<div class="container edit text-center" id="{item.id}">
  	<i class="{item.icon} fa-big"></i>
  	<h1>{item.title}</h1>
  	<p>{item.subtitle}</p>
  	<a href="{item.button_link}" class="btn btn-outline-dark mt-5">{item.button_text}</a>
	</div>
</section>
{/if}