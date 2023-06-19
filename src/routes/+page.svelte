<script lang="ts">

    export let data;
</script>

<h2>My cool user list</h2>
<ul>
    {#each data.users as user}
        <li>
            {user.id} - {`${user.username}`}
        </li>
    {/each}
</ul>


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

