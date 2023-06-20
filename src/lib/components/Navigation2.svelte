<script lang="ts">
	import { drawerStore } from '@skeletonlabs/skeleton';

	function drawerClose(): void {
		drawerStore.close();
	}
</script>


<nav class="list-nav p-4">
	<ul>
		<li><a href="/layer/setting/" on:click={drawerClose} style="margin-bottom: 25px;">Privatsphäre</a></li>
        <li><a href="/layer/setting/mail" on:click={drawerClose} style="margin-bottom: 25px;">Benachrichtigung</a></li>
        <li><a href="/layer/setting/profilsetting" on:click={drawerClose} style="margin-bottom: 25px;">Profileinstellungen</a></li>
        <li><a href="/layer/setting/abmelden" on:click={drawerClose} style="margin-bottom: 25px;">Abmelden</a></li>
        <li><a href="/layer/setting/löschen" on:click={drawerClose} style="margin-bottom: 25px;">Account löschen</a></li>
	</ul>
</nav>




<style>

	</style>