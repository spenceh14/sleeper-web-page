<script>
  import { onMount } from 'svelte';

  let iframe;
  
  onMount(() => {
    iframe.onload = () => {
      try {
        const iframeDocument = iframe.contentDocument || iframe.contentWindow.document;
        const button = iframeDocument.getElementById('dont-know');
        if (button) {
          button.click();
        } else {
          console.error('Button not found in the iframe.');
        }
      } catch (error) {
        console.error('Error accessing iframe content:', error);
      }
    };
  });
</script>
<div class="holder">
<iframe bind:this={iframe} src="https://keeptradecut.com/dynasty/power-rankings/league-overview?leagueId=1048240987706941440&platform=2" id="ktc-rankings" />

</div>
