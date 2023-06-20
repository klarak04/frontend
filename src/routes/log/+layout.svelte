<script lang="ts">
	// The ordering of these imports is critical to your app working properly
	// If you have source.organizeImports set to true in VSCode, then it will auto change this ordering
	import '@skeletonlabs/skeleton/styles/all.css';
	// Most of your app wide CSS should be put in this file
	import {
		AppBar,
		AppShell,
		Avatar,
		Drawer,
		Modal,
		Toast,
		drawerStore
	} from '@skeletonlabs/skeleton';
	

	function drawerOpen(): void {
		drawerStore.open();
	}
	import { LightSwitch } from '@skeletonlabs/skeleton';
	export let year = new Date().getFullYear();
</script>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">


<AppShell slotSidebarLeft="w-0 md:w-52 bg-surface-500/10">
	<svelte:fragment slot="header">
	<div class = "shadow">

		<AppBar gridColumns="grid-cols-3" slotDefault="place-self-center" slotTrail="place-content-end">		
			<svelte:fragment slot="lead">
				<button class="md:hidden btn btn-sm mr-4" on:click={drawerOpen}>
					<span>
						<svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
							<rect width="100" height="20" />
							<rect y="30" width="100" height="20" />
							<rect y="60" width="100" height="20" />
						</svg>
					</span>
				</button>
					
					<img src="https://byrio.org/wp-content/uploads/2018/06/BYRIO-Big-Round-1024x1024.png" alt="Beschreibung des Bildes" width="55" height="55">
			</svelte:fragment>
			
			<div class = "willkommen">
				
				<p>Willkommen</p>
				<p>bei LinkUp&nbsp;<i class="fa fa-exclamation" aria-hidden="true"></i></p>
			</div>
			

			<svelte:fragment slot="trail">
				<LightSwitch />
			</svelte:fragment>
			

				
		</AppBar>


		</div>
	</svelte:fragment>
	

	<div class="container p-10 mx-auto">
		<slot />
	</div>

	<svelte:fragment slot="footer">
		<div class = "foot">
    		<a href="/log/impressum2">Impressum</a>
    		<a href="/log/datenschutzrichtlinien2">Datenschutz</a>
    		<a href="/log/nutzungsrichtlinien2">Nutzungsrichtlinien</a>
  		<p>&copy; {year} LinkUp. Alle Rechte vorbehalten.</p>
		</div>
	</svelte:fragment>

	
</AppShell>





				



<style>
	.shadow{
		box-shadow: 0 0 4px 0 rgba(0.9, 0.9, 0.9, 0.2), 0 4px 18px 0 rgba(0, 0, 0, 0.2);
	}

	.foot{
		text-align: center;
		font-size: 13px;
		margin: 20px;
	}

	.pageheader{
		text-align: center;
		font-size: 13px;
		margin: 0 20px;
		font-size: 40px;
		font-family: cursive;
		color: #6fa1bf;
	}

	.willkommen p{
		font-size: 40px;
		font-family: cursive;
		color: #94d6ff;
		text-align: center;
		margin-top: 10px;
	}



</style>
