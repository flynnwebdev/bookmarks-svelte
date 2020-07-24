<script>
  import { bookmarks } from "./stores";
  import { navigate } from "svelte-routing";
  import api from "./api"

  let title = "";
  let url = "";
  let description = "";

  const onSubmit = async e => {
    e.preventDefault();
    const bookmark = { title, url, description };
    api.post("bookmarks", bookmark);
    bookmarks.update(current => [...current, bookmark]);
    navigate("/bookmarks");
  };
</script>

<div className="container">
  <form on:submit={onSubmit}>
    <label for="title">Title</label>
    <input id="title" bind:value={title} />
    <label for="url">URL</label>
    <input id="url" bind:value={url} />
    <label for="description">Description</label>
    <textarea id="description" cols="30" rows="10" bind:value={description} />
    <p>
      <button>Create</button>
    </p>
  </form>
</div>
