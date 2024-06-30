<script>
  import { onMount } from 'svelte';

  let iframe;

  onMount(() => {
    iframe.onload = () => {
      try {
        const iframeDocument = iframe.contentDocument || iframe.contentWindow.document;

        // Wait for the DOM inside the iframe to be fully loaded
        const checkButton = setInterval(() => {
          const button = iframeDocument.querySelector('span#dont-know');
          if (button) {
            button.click();
            clearInterval(checkButton);
          } else {
            console.error('Button not found in the iframe.');
          }
        }, 1000); // Check every second
      } catch (error) {
        console.error('Error accessing iframe content:', error);
      }
    };
  });
</script>
<div class="holder">
<iframe 
  bind:this={iframe} 
  src=https://keeptradecut.com/dynasty/power-rankings/league-overview?leagueId=1048240987706941440&platform=2" 
  id="ktc-pos-rank-iframe" 
  style="width: 800px; height: 600px; overflow: auto;" 
/>

</div>
