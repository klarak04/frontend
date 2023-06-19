<script lang="ts">
	import { onMount } from 'svelte';
	import { writable } from 'svelte/store';
    import 'material-icons/iconfont/material-icons.css';
	import {Avatar,} from '@skeletonlabs/skeleton';

	export let posts = writable<{ id: number; user: string; createdAt: string; content: string; isFavorite: boolean; likes: number }[]>([]);

	export let writing = '';
	let id = 1;
	export let user = 'Klara';
	export let createdAt = '12-09-2023';

	export const toggleFavorite = (post: { id: number; user: string; createdAt: string; content: string; isFavorite: boolean; likes: number }) => {
		post.isFavorite = !post.isFavorite;
		if (post.isFavorite) {
			post.likes++;
		} else {
			post.likes--;
		}
		posts.update((value) => [...value]);
	};

	onMount(() => {});

	export const handlePost = () => {
		if (writing.trim() !== '') {
			const newPost = {
				id: id++,
				user: user,
				createdAt: createdAt,
				content: writing,
				isFavorite: false,
				likes: 0,
			};
			posts.update((value) => [...value, newPost]);
			writing = '';
		}
	};
    	//export let data;
</script>



<div class="container h-full mx-auto gap-8" style="margin-bottom: 8vh;">
	<form class="card p-4 flex flex-col gap-3" style="width: 60vh;">
		<h2>Neuer Post</h2>
		<textarea bind:value={writing} class="textarea" rows="4" placeholder="Dein Post..." />
		<button type="button" class="btn variant-ghost-primary self-end" on:click={handlePost}>Posten</button>
	</form>
</div>

{#each $posts as post (post.id)}
	<div class="card p-4 flex flex-col gap-3">
		<div class="postheader">
			<Avatar initials={user} background="bg-primary-500" width="w-9" class="mr-4"/>
			<strong style="margin-right: 6vh;">{post.user}</strong> {post.createdAt}
		</div>
		<div style="margin-left: 1vh;">{post.content}</div>
		<div class="actions">
			<button type="button" class="btn-icon !bg-transparent" on:click={() => toggleFavorite(post)}>
				{#if post.isFavorite}
					<span class="material-icons-outlined">favorite</span>
				{:else}
					<span class="material-icons-outlined">favorite_border</span>
				{/if}
			</button>
			<h3 class="counter">{post.likes}</h3>
			<button type="button" class="btn-icon !bg-transparent">
				<span class="material-symbols-outlined">chat_bubble</span>
			</button>
		</div>
	</div>
{/each}

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

    .card {
		margin-bottom: 1rem; 
	}
</style>


<!-- <h2>My cool user list</h2>
<ul>
    {#each data.users as user}
        <li>
            {user.id} - {`${user.username}`}
        </li>
    {/each}
</ul> -->


<!-- <form method="post">
    <input type="hidden" name="id" value={task.id} />
    <input
        type="checkbox"
        name="completed"
        checked={task.completed}
    />
    {task.id} - {`${task.name}: ${task.description}`}
    <button formaction="?/update">Update</button>
</form> -->

