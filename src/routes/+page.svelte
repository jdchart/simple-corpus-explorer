<script>
    import { base } from '$app/paths';
    import MenuButton from '$lib/components/MenuButton.svelte';
    let slice_data = []

    import AudioPlayer from '$lib/components/AudioPlayer.svelte';
    import JsonInput from '$lib/components/JsonInput.svelte';

    import SoundPlot from '$lib/components/SoundPlot.svelte';

    function update_json(e){
        slice_data = e.detail.data["slices"];
        slice_data = slice_data;
        console.log(slice_data)
    }
</script>

<div class="container">
    <div class="inner_container">
        <SoundPlot />
    </div>
    
</div>

<style>
    .input_files{
        display: flex;
        flex-wrap: wrap;
        padding: 1em;
        width: 100%;
        background-color: grey;
        gap: 1em;
    }
</style>