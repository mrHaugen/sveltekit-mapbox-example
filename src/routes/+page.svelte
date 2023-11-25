<script lang="ts">
	import { Map, Marker } from '@beyonk/svelte-mapbox';
	import { PUBLIC_MAPBOX_TOKEN } from '$env/static/public';

	let markers = [{ lat: 59.917099, lng: 10.727547 }];

	let mapComponent: any;
	let initialZoomLevel = 19;
	let mapCenter = [10.727547, 59.917];

</script>

<div class="relative h-screen w-full">
	<Map
		accessToken={PUBLIC_MAPBOX_TOKEN}
		style="mapbox://styles/mapbox/outdoors-v11"
		bind:this={mapComponent}
		bind:zoom={initialZoomLevel}
		center={mapCenter}
	>
		{#each markers as marker}
			<Marker lat={marker.lat} lng={marker.lng} markerOffset={[0, 0]} popup={false}>
				<!-- prettier-ignore -->
				<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-plus-circle"><circle cx="12" cy="12" r="10"/><path d="M8 12h8"/><path d="M12 8v8"/></svg>
			</Marker>
			<Marker lat={marker.lat} lng={marker.lng} markerOffset={[0, -20]} popup={false}>
				<!-- prettier-ignore -->
				<svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-map-pin"><path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"/><circle cx="12" cy="10" r="3"/></svg>
			</Marker>
		{/each}
	</Map>

	<div class="absolute top-5 ml-5 w-3/4">
		<a class="bg-white p-2" href="/">sveltekit-mapbox-example by brage@1618.no</a>
	</div>
</div>
