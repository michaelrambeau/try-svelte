<script>
  export let size = 50;
  export let project;

  import { getProjectAvatarURL } from "../app/projects";

  let url;

  $: {
    url = getProjectAvatarURL(project, size);
  }
</script>

<img src={url} width={size} height={size} alt={project.name} />
