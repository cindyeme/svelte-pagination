<script>
	import Header from "./components/Header.svelte";
	import CardLayout from "./components/CardLayout.svelte";
	import CardItem from "./components/CardItem.svelte";
	import { paginate, LightPaginationNav } from 'svelte-paginate';
	import Overlay from "./components/Overlay.svelte";

  let items = [];
  let currentPage = 1;
  let pageSize = 6;
	let allOperations = [];

	(async () => {
		const response = await fetch("https://jsonplaceholder.typicode.com/photos");
		const posts = await response.json();
		items = posts;
	})();

  $: paginatedItems = paginate({ items, pageSize, currentPage })

</script>

<main>
	<Header />
	<div class="container">
		<CardLayout>
			{#await paginatedItems}
				<Overlay />
			{:then items}
				{#each items as item}
					<CardItem item={item} />
				{/each}
			{/await}
		</CardLayout>
		
		{#await paginatedItems}
			<div>loading...</div>
		{:then paginatedItems}
			<div class="pagination">
				<LightPaginationNav
					totalItems="{items.length}"
					pageSize="{pageSize}"
					currentPage="{currentPage}"
					limit="{1}"
					showStepOptions="{true}"
					on:setPage="{(e) => currentPage = e.detail.page}"
				/>
			</div>
		{/await}
	</div>
</main>