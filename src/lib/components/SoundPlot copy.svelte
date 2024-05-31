<script>
    import { onMount } from 'svelte';
    import * as d3 from 'd3';
  
    export let data = [];
    import { writable } from 'svelte/store';

    // Store to hold the data
    const dataStore = writable([]);

  
    onMount(() => {
      const svg = d3.select('#scatter-plot')
        .attr('width', 500)
        .attr('height', 500);
  
      const xScale = d3.scaleLinear()
        .domain([0, d3.max(data, d => d.x)])
        .range([0, 500]);
  
      const yScale = d3.scaleLinear()
        .domain([0, d3.max(data, d => d.y)])
        .range([500, 0]);
  
      svg.selectAll('circle')
        .data(data)
        .enter()
        .append('circle')
        .attr('cx', d => xScale(d.x))
        .attr('cy', d => yScale(d.y))
        .attr('r', 5)
        .attr('fill', 'blue')
        .on('click', function(event, d) {
          console.log(d.start, d.end);
        });
    });


  </script>
  
  <svg id="scatter-plot"></svg>

  
  <style>
    svg {
      border: 1px solid black;
    }
  </style>
  