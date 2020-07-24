<script>
  import { bookmarks } from "./stores.js";
  import { Link } from 'svelte-routing'
</script>

<h1>Bookmarks</h1>
<Link to="/bookmarks/new">New Bookmark</Link>
{#each $bookmarks as bookmark}
  <article>
    <h3>{bookmark.title}</h3>
    <p>{bookmark.description}</p>
    <a href={bookmark.url} target="_blank">{bookmark.url}</a>
  </article>
{/each}
