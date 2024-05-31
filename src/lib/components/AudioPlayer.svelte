<script>
    let audioPlayer;
  
    function handleFileSelect(event) {
      const file = event.target.files[0];
      const reader = new FileReader();
  
      reader.onload = function(event) {
        const audioContext = new AudioContext();
        const audioData = event.target.result;
  
        audioContext.decodeAudioData(audioData, function(buffer) {
          const source = audioContext.createBufferSource();
          source.buffer = buffer;
          source.connect(audioContext.destination);
          source.start();
        });
      };
  
      reader.readAsArrayBuffer(file);
    }
</script>

<input type="file" accept="audio/*" on:change={handleFileSelect}>


<style>

</style>