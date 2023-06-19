<script lang="ts">
    import { onMount } from 'svelte';
	import 'material-icons/iconfont/material-icons.css';
	import { writable } from 'svelte/store';

	export let tabSet: number = 0;
	export let user = 'Klara';

	export let content = 'Hallo';
	export let createdAt = '12-09-2023';
	let id = 1;
	export let isFavorite = false;
	export let likes = writable(0);

	export const handleTabChange = (event: CustomEvent<number>) => {
    tabSet = event.detail;
  };
	
    export const toggleFavorite = () => {
    isFavorite = !isFavorite;
	if (isFavorite) {
		likes.update((value) => value +1)
	} else {
		likes.update((value) => value - 1);
	}
    };	

	onMount(() => {
    
  });
</script>

<div class="card p-4 flex flex-col gap-3">
    <div class="postheader"><strong style="margin-right: 6vh;">{user}</strong> {createdAt}</div>	

    <div style="margin-left: 1vh;">{content}</div>
    <div class="actions">
        <button type="button" class="btn-icon !bg-transparent" on:click={toggleFavorite}>
            {#if isFavorite}
              <span class="material-icons-outlined">favorite</span>
            {:else}
              <span class="material-icons-outlined">favorite_border</span>
            {/if}
          </button>	
          <h3 class="counter">{$likes}</h3>
          <button type="button" class="btn-icon !bg-transparent">
            <span class="material-symbols-outlined">chat_bubble</span>
          </button>
    </div>	
</div>
<style>

	.postheader {
		display: flex;
		text-align: left;
		margin-left: 1vh;
	}


	.actions {
		display: flex;
		text-align: left;
	}

	.counter {
		margin-top: 5px;
	}

</style>