<script>
  import { setContext, onMount } from "svelte";
  import { bookmarks } from "./stores.js";
  import { Router, Route, Link } from "svelte-routing";
  import Bookmarks from "./Bookmarks.svelte";
  import CreateBookmark from "./CreateBookmark.svelte";
  import Home from "./Home.svelte";
  import api from "./api"

  onMount(async () => {
    const res = await api.get("bookmarks")
    bookmarks.set(res.data)
  });
</script>

<main>
  <Router>
    <nav>
      <Link to="/">Home</Link>
      <Link to="/bookmarks">Bookmarks</Link>
    </nav>
    <div>
      <Route path="/" component={Home} />
      <Route path="/bookmarks" component={Bookmarks} />
      <Route path="/bookmarks/new" component={CreateBookmark} />
    </div>
  </Router>
</main>
