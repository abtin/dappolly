<script>
    import {fade, scale} from "svelte/transition";
    import {flip} from "svelte/animate";
    import PollDetails from "./PollDetails.svelte";
    import PollStore from "../stores/PollStore";
    // import {onDestroy, onMount} from "svelte";
    // export let polls = [];
    // const unsub = PollStore.subscribe((data) => {
    //     polls = data;
    // });
    // onMount(() => {
    //     // get the data from DB
    //     console.log('store mounted');
    // });
    //onDestroy(() => {
    //    console.log('store destroyed');
    //    unsub();
    // });
</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <div in:fade out:scale|local animate:flip={{duration: 500}}>
            <PollDetails {poll}/>
        </div>

    {/each}
</div>

<style>
    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }

</style>