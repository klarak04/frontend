<script lang="ts">
    import { TabGroup, Tab } from '@skeletonlabs/skeleton';
    let tabSet: number = 0;
	import {Avatar,} from '@skeletonlabs/skeleton';
	let user = 'KK';
</script>

<div class="user">
	<Avatar initials={user} width="w-12" background="bg-primary-500" />
	<div class="user-info">
		<span>Klara Kulinna</span>
		<span>@KK</span>
	</div>
</div>

<div class="Tabs">
    
<TabGroup justify="justify-center" padding="px-20 py-3">
	<Tab bind:group={tabSet} name="tab1" value={0}>Posts</Tab>
	<Tab bind:group={tabSet} name="tab2" value={1}>Follower</Tab>
	<Tab bind:group={tabSet} name="tab3" value={2}>Likes</Tab>
	<!-- Tab Panels --->
	<svelte:fragment slot="panel">
		{#if tabSet === 0}
			(tab panel 1 contents)
		{:else if tabSet === 1}
			(tab panel 2 contents)
		{:else if tabSet === 2}
			(tab panel 3 contents)
		{/if}
	</svelte:fragment>
</TabGroup>
			
</div>

<style>
	.user {
        display: flex;
        align-items: center;
    }

    .user-info {
        margin-left: 8px;
    }
</style>
