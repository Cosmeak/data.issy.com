<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import ApexCharts from 'apexcharts';

	// Props
	export let options: Object = {}; // For all options available, please refer to this official documentation: https://apexcharts.com/docs/options/#
	export let type: String = 'line';
	export let series: Array<any>;
	export let width: String = '100%';
	export let height: String = 'auto';

	// Utils
	let container: HTMLElement | undefined = undefined;
	let chart: ApexCharts | undefined = undefined;

	// Lyfecicle hooks
	onMount(() => {
		init();
	});

	onDestroy(() => {
		chart?.destroy();
		chart = undefined;
	});

	// Functions
	function init() {
		const chartOptions = {
			chart: {
				type,
				height,
				width,
				events: {} // TODO: events handling and dispatch
			},
			series,
			...options
		};

		chart = new ApexCharts(container, chartOptions);
		chart.render();
	}
	// -- TODO: add events handling and api function from apexcharts lib
</script>

<div bind:this={container} />
