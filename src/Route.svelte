<script>
  import { Route } from "svelte-navigator";

  export let path;
</script>

<Route {path} let:params let:location let:navigate>

    <slot {params} {location} {navigate} />

</Route>