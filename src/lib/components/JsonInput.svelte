<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    let jsonData = null;

    async function handleFileSelect(event) {
        const file = event.target.files[0];
        const reader = new FileReader();

        reader.onload = function(event) {
        const jsonString = event.target.result;
        try {
            jsonData = JSON.parse(jsonString);
            //console.log("JSON Data:", jsonData);

            dispatch('update_json_data', {
                data: jsonData
            });
        } catch (error) {
            console.error("Error parsing JSON:", error);
        }
    };

    reader.readAsText(file);
}
</script>

<input type="file" accept=".json" on:change={handleFileSelect}>

<style>

</style>
