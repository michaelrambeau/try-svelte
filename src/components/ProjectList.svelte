<script>
  export let projects = [];
  export let count = 10;

  import ProjectAvatar from "./ProjectAvatar.svelte";

  let paginatedProjects = [];
  $: {
    paginatedProjects = projects.slice(0, 100);
  }
</script>

<table>
  {#each paginatedProjects as project (project.name)}
    <tr>
      <td>
        <ProjectAvatar {project} />
      </td>
      <td>{project.name}</td>
      <td>{project.description}</td>
      <td>{project.tags}</td>
    </tr>
  {/each}
</table>
