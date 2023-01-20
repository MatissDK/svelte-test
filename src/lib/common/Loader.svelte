<script lang="ts">
    import {createEventDispatcher, onMount} from "svelte";

    // output
    const dispatch = createEventDispatcher();

    let startValue: number = 20;
    let interval;

    onMount(() => navigate());

    function navigate(): void {
        startValue = 0;
        interval = setInterval(increment, 50);

        setTimeout(() => {
            dispatch('display', false);
            clearInterval(interval);
        }, 500);
    }

    function increment() {
        startValue = startValue + 20;
    }
</script>


<progress class="progress progress-info h-1 absolute top-0 left-0 right-0 z-10 w-full" value="{startValue}"
          max="100"></progress>