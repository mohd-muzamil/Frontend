<script>
	// import * as d3 from 'd3';
	import { onMount } from 'svelte';

	let headerText;

	let name = '';
	// 	let data =[
	// 		[0, 0],
	// 		[1, 2],
	// 		[5, 5]
	// 	]
	let data = [
		['sepal.length', 'sepal.width', 'petal.length', 'petal.width', 'variety'],
		[5.1, 3.5, 1.4, 0.2, 'Setosa'],
		[4.9, 3, 1.4, 0.2, 'Setosa'],
		[4.7, 3.2, 1.3, 0.2, 'Setosa'],
		[4.6, 3.1, 1.5, 0.2, 'Setosa'],
		[5, 3.6, 1.4, 0.2, 'Setosa'],
		[5.4, 3.9, 1.7, 0.4, 'Setosa'],
		[4.6, 3.4, 1.4, 0.3, 'Setosa'],
		[5, 3.4, 1.5, 0.2, 'Setosa'],
		[4.4, 2.9, 1.4, 0.2, 'Setosa'],
		[4.9, 3.1, 1.5, 0.1, 'Setosa'],
		[5.4, 3.7, 1.5, 0.2, 'Setosa'],
		[4.8, 3.4, 1.6, 0.2, 'Setosa'],
		[4.8, 3, 1.4, 0.1, 'Setosa'],
		[4.3, 3, 1.1, 0.1, 'Setosa'],
		[5.8, 4, 1.2, 0.2, 'Setosa'],
		[5.7, 4.4, 1.5, 0.4, 'Setosa'],
		[5.4, 3.9, 1.3, 0.4, 'Setosa'],
		[5.1, 3.5, 1.4, 0.3, 'Setosa'],
		[5.7, 3.8, 1.7, 0.3, 'Setosa'],
		[5.1, 3.8, 1.5, 0.3, 'Setosa'],
		[5.4, 3.4, 1.7, 0.2, 'Setosa'],
		[5.1, 3.7, 1.5, 0.4, 'Setosa'],
		[4.6, 3.6, 1, 0.2, 'Setosa'],
		[5.1, 3.3, 1.7, 0.5, 'Setosa'],
		[4.8, 3.4, 1.9, 0.2, 'Setosa'],
		[5, 3, 1.6, 0.2, 'Setosa'],
		[5, 3.4, 1.6, 0.4, 'Setosa'],
		[5.2, 3.5, 1.5, 0.2, 'Setosa'],
		[5.2, 3.4, 1.4, 0.2, 'Setosa'],
		[4.7, 3.2, 1.6, 0.2, 'Setosa'],
		[4.8, 3.1, 1.6, 0.2, 'Setosa'],
		[5.4, 3.4, 1.5, 0.4, 'Setosa'],
		[5.2, 4.1, 1.5, 0.1, 'Setosa'],
		[5.5, 4.2, 1.4, 0.2, 'Setosa'],
		[4.9, 3.1, 1.5, 0.2, 'Setosa'],
		[5, 3.2, 1.2, 0.2, 'Setosa'],
		[5.5, 3.5, 1.3, 0.2, 'Setosa'],
		[4.9, 3.6, 1.4, 0.1, 'Setosa'],
		[4.4, 3, 1.3, 0.2, 'Setosa'],
		[5.1, 3.4, 1.5, 0.2, 'Setosa'],
		[5, 3.5, 1.3, 0.3, 'Setosa'],
		[4.5, 2.3, 1.3, 0.3, 'Setosa'],
		[4.4, 3.2, 1.3, 0.2, 'Setosa'],
		[5, 3.5, 1.6, 0.6, 'Setosa'],
		[5.1, 3.8, 1.9, 0.4, 'Setosa'],
		[4.8, 3, 1.4, 0.3, 'Setosa'],
		[5.1, 3.8, 1.6, 0.2, 'Setosa'],
		[4.6, 3.2, 1.4, 0.2, 'Setosa'],
		[5.3, 3.7, 1.5, 0.2, 'Setosa'],
		[5, 3.3, 1.4, 0.2, 'Setosa'],
		[7, 3.2, 4.7, 1.4, 'Versicolor'],
		[6.4, 3.2, 4.5, 1.5, 'Versicolor'],
		[6.9, 3.1, 4.9, 1.5, 'Versicolor'],
		[5.5, 2.3, 4, 1.3, 'Versicolor'],
		[6.5, 2.8, 4.6, 1.5, 'Versicolor'],
		[5.7, 2.8, 4.5, 1.3, 'Versicolor'],
		[6.3, 3.3, 4.7, 1.6, 'Versicolor'],
		[4.9, 2.4, 3.3, 1, 'Versicolor'],
		[6.6, 2.9, 4.6, 1.3, 'Versicolor'],
		[5.2, 2.7, 3.9, 1.4, 'Versicolor'],
		[5, 2, 3.5, 1, 'Versicolor'],
		[5.9, 3, 4.2, 1.5, 'Versicolor'],
		[6, 2.2, 4, 1, 'Versicolor'],
		[6.1, 2.9, 4.7, 1.4, 'Versicolor'],
		[5.6, 2.9, 3.6, 1.3, 'Versicolor'],
		[6.7, 3.1, 4.4, 1.4, 'Versicolor'],
		[5.6, 3, 4.5, 1.5, 'Versicolor'],
		[5.8, 2.7, 4.1, 1, 'Versicolor'],
		[6.2, 2.2, 4.5, 1.5, 'Versicolor'],
		[5.6, 2.5, 3.9, 1.1, 'Versicolor'],
		[5.9, 3.2, 4.8, 1.8, 'Versicolor'],
		[6.1, 2.8, 4, 1.3, 'Versicolor'],
		[6.3, 2.5, 4.9, 1.5, 'Versicolor'],
		[6.1, 2.8, 4.7, 1.2, 'Versicolor'],
		[6.4, 2.9, 4.3, 1.3, 'Versicolor'],
		[6.6, 3, 4.4, 1.4, 'Versicolor'],
		[6.8, 2.8, 4.8, 1.4, 'Versicolor'],
		[6.7, 3, 5, 1.7, 'Versicolor'],
		[6, 2.9, 4.5, 1.5, 'Versicolor'],
		[5.7, 2.6, 3.5, 1, 'Versicolor'],
		[5.5, 2.4, 3.8, 1.1, 'Versicolor'],
		[5.5, 2.4, 3.7, 1, 'Versicolor'],
		[5.8, 2.7, 3.9, 1.2, 'Versicolor'],
		[6, 2.7, 5.1, 1.6, 'Versicolor'],
		[5.4, 3, 4.5, 1.5, 'Versicolor'],
		[6, 3.4, 4.5, 1.6, 'Versicolor'],
		[6.7, 3.1, 4.7, 1.5, 'Versicolor'],
		[6.3, 2.3, 4.4, 1.3, 'Versicolor'],
		[5.6, 3, 4.1, 1.3, 'Versicolor'],
		[5.5, 2.5, 4, 1.3, 'Versicolor'],
		[5.5, 2.6, 4.4, 1.2, 'Versicolor'],
		[6.1, 3, 4.6, 1.4, 'Versicolor'],
		[5.8, 2.6, 4, 1.2, 'Versicolor'],
		[5, 2.3, 3.3, 1, 'Versicolor'],
		[5.6, 2.7, 4.2, 1.3, 'Versicolor'],
		[5.7, 3, 4.2, 1.2, 'Versicolor'],
		[5.7, 2.9, 4.2, 1.3, 'Versicolor'],
		[6.2, 2.9, 4.3, 1.3, 'Versicolor'],
		[5.1, 2.5, 3, 1.1, 'Versicolor'],
		[5.7, 2.8, 4.1, 1.3, 'Versicolor'],
		[6.3, 3.3, 6, 2.5, 'Virginica'],
		[5.8, 2.7, 5.1, 1.9, 'Virginica'],
		[7.1, 3, 5.9, 2.1, 'Virginica'],
		[6.3, 2.9, 5.6, 1.8, 'Virginica'],
		[6.5, 3, 5.8, 2.2, 'Virginica'],
		[7.6, 3, 6.6, 2.1, 'Virginica'],
		[4.9, 2.5, 4.5, 1.7, 'Virginica'],
		[7.3, 2.9, 6.3, 1.8, 'Virginica'],
		[6.7, 2.5, 5.8, 1.8, 'Virginica'],
		[7.2, 3.6, 6.1, 2.5, 'Virginica'],
		[6.5, 3.2, 5.1, 2, 'Virginica'],
		[6.4, 2.7, 5.3, 1.9, 'Virginica'],
		[6.8, 3, 5.5, 2.1, 'Virginica'],
		[5.7, 2.5, 5, 2, 'Virginica'],
		[5.8, 2.8, 5.1, 2.4, 'Virginica'],
		[6.4, 3.2, 5.3, 2.3, 'Virginica'],
		[6.5, 3, 5.5, 1.8, 'Virginica'],
		[7.7, 3.8, 6.7, 2.2, 'Virginica'],
		[7.7, 2.6, 6.9, 2.3, 'Virginica'],
		[6, 2.2, 5, 1.5, 'Virginica'],
		[6.9, 3.2, 5.7, 2.3, 'Virginica'],
		[5.6, 2.8, 4.9, 2, 'Virginica'],
		[7.7, 2.8, 6.7, 2, 'Virginica'],
		[6.3, 2.7, 4.9, 1.8, 'Virginica'],
		[6.7, 3.3, 5.7, 2.1, 'Virginica'],
		[7.2, 3.2, 6, 1.8, 'Virginica'],
		[6.2, 2.8, 4.8, 1.8, 'Virginica'],
		[6.1, 3, 4.9, 1.8, 'Virginica'],
		[6.4, 2.8, 5.6, 2.1, 'Virginica'],
		[7.2, 3, 5.8, 1.6, 'Virginica'],
		[7.4, 2.8, 6.1, 1.9, 'Virginica'],
		[7.9, 3.8, 6.4, 2, 'Virginica'],
		[6.4, 2.8, 5.6, 2.2, 'Virginica'],
		[6.3, 2.8, 5.1, 1.5, 'Virginica'],
		[6.1, 2.6, 5.6, 1.4, 'Virginica'],
		[7.7, 3, 6.1, 2.3, 'Virginica'],
		[6.3, 3.4, 5.6, 2.4, 'Virginica'],
		[6.4, 3.1, 5.5, 1.8, 'Virginica'],
		[6, 3, 4.8, 1.8, 'Virginica'],
		[6.9, 3.1, 5.4, 2.1, 'Virginica'],
		[6.7, 3.1, 5.6, 2.4, 'Virginica'],
		[6.9, 3.1, 5.1, 2.3, 'Virginica'],
		[5.8, 2.7, 5.1, 1.9, 'Virginica'],
		[6.8, 3.2, 5.9, 2.3, 'Virginica'],
		[6.7, 3.3, 5.7, 2.5, 'Virginica'],
		[6.7, 3, 5.2, 2.3, 'Virginica'],
		[6.3, 2.5, 5, 1.9, 'Virginica'],
		[6.5, 3, 5.2, 2, 'Virginica'],
		[6.2, 3.4, 5.4, 2.3, 'Virginica'],
		[5.9, 3, 5.1, 1.8, 'Virginica']
	];

	let data_json = {};
	data_json.x = data.slice(1).map((d) => d[0]);
	data_json.y = data.slice(1).map((d) => d[1]);
	data_json.mode = 'markers';
	data_json.type = 'scatter';
	console.log(data_json);

	onMount(() => {
		headerText = 'On Mount Called !';
		let plotDiv = document.getElementById('plotDiv');
		let Plot = new Plotly.newPlot(plotDiv, [data_json], {}, { showSendToCloud: true });
	});

	// var x_min = 0;
	// var x_max = 0;
	// var y_min = 0;
	// var y_max = 0;
	// data.forEach((d) => {
	// 	x_min = d[0] < x_min ? d[0] : x_min;
	// 	x_max = d[0] > x_max ? d[0] : x_max;
	// 	y_min = d[1] < y_min ? d[1] : y_min;
	// 	y_max = d[1] > y_max ? d[1] : y_max;
	// });

	// let width = 500;
	// let height = 300;
	// let x = d3
	// 	.scaleLinear()
	// 	.domain([x_min, x_max]) // unit: km
	// 	.range([0, width]); // unit: pixels
	// let y = d3
	// 	.scaleLinear()
	// 	.domain([y_min, y_max]) // unit: km
	// 	.range([0, height]); // unit: pixels
</script>

<svelte:head>
	<script src="https://cdn.plot.ly/plotly-latest.min.js" type="text/javascript"></script>
</svelte:head>
<input id="name" placeholder="Enter your Name" bind:value={name} />
<!-- <button on:click={click}>submit</button> -->

<h1>Hello {name}</h1>

<!-- <div id="a1">
	<svg width="500" height="300" style="border:1px solid black">
		{#each data as i}
			<circle cx={x(i[0])} cy={y(i[1])} r="5" fill="red" />
		{/each}
	</svg>
</div> -->

<h3>{headerText}</h3>
<div id="plotly">
	<div>
		<h3>Iris scatter plot</h3>
	</div>
	<div id="plotDiv"><!-- Plotly chart will be drawn inside this DIV --></div>
</div>

<style>
</style>
