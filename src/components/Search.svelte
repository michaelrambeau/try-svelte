<script>
  import { filterProjectsByQuery } from "../app/projects";
  import ProjectList from "./ProjectList.svelte";
  import SearchBox from "./SearchBox.svelte";

  export let projects;

  const searchOptions = {
    query: "",
    showOnlyFeaturedProjects: false
  };

  let filteredeProjects = projects;

  function handleChangeQuery(event) {
    const query = event.detail.query;
    searchOptions.query = query;
  }

  $: {
    filteredeProjects = filterProjectsByQuery(
      projects,
      searchOptions.query
    ).filter(project => {
      if (!searchOptions.showOnlyFeaturedProjects) return true;
      return !!project.icon;
    });
  }
</script>

<div>
  <SearchBox on:message={handleChangeQuery} />
  <label>
    <input
      type="checkbox"
      bind:checked={searchOptions.showOnlyFeaturedProjects} />
    <span class="checkable">Show only featured projects</span>
  </label>
  <h4>{filteredeProjects.length} projects found</h4>
  {#if filteredeProjects.length > 0}
    <ProjectList projects={filteredeProjects} />
  {:else}
    <div>No projects found!</div>
  {/if}
</div>
