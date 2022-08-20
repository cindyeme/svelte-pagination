<script>
  import {BlogStore} from '../stores'
  import CardItem from "./CardItem.svelte";
  import CardLayout from './CardLayout.svelte';
</script>

<CardLayout>
  {#each $BlogStore as item (item.id)}
    <CardItem item={item} />
  {/each}
</CardLayout>