


    <script>
        import { onMount } from 'svelte';
        // import { Network } from 'vis-network/standalone';
        import { Network } from '../../node_modules/vis-network/standalone/esm/vis-network';

      
        let container;
        let network;
      
        onMount(() => {
          const data = {
            nodes: [
              { id: 1, label: 'Me' },
              { id: 2, label: 'Flutter' },
              { id: 3, label: 'OTT App' },
            ],
            edges: [
              { from: 1, to: 2 },
              { from: 2, to: 3 },
            ]
          };
      
          const options = {
            nodes: { shape: 'dot', size: 16 },
            edges: { arrows: 'to' },
            physics: { stabilization: false },
          };
      
          network = new Network(container, data, options);
        });
      </script>
      
      <div bind:this={container} style="height: 600px;"></div>
      



