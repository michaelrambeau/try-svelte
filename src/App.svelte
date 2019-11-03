<script>
  import ProjectList from "./components/ProjectList.svelte";
  import Search from "./components/Search.svelte";

  import { fetchProjects, filterProjectsByQuery } from "./app/projects";

  let data = fetchProjects();
</script>

<style>
  .container {
    max-width: 800px;
    margin: 0 auto;
  }
</style>

<div class="container">
  <h1>Best of JavaScript + Svelte</h1>

  {#await data}
    <div>Loading</div>
  {:then projects}
    <Search {projects} />
  {/await}
</div>
