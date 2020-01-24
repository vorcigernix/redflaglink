<script context="module">
  export function preload({ host, params, query }) {
    return this.fetch(`https://` + host + `/sinners.json`)
      .then(r => r.json())
      .then(posts => {
        return { posts };
      });
  }
</script>

<script>
  export let posts;
</script>

<style>
  a {
    text-decoration: none;
  }
  ul {
    margin: 0 0 1em 0;
    line-height: 1.5;
	list-style-type: none;
	padding-inline-start: 0px;
  }
  li {
    box-shadow: 0px 2px 1px -1px rgba(0, 0, 0, 0.2),
      0px 1px 1px 0px rgba(0, 0, 0, 0.14), 0px 1px 3px 0px rgba(0, 0, 0, 0.12);
    border-radius: 4px;
    flex-direction: column;
    box-sizing: border-box;
    padding: 16px;
    margin: 1rem 0;
  }
  .cmpname {
    margin: 0 0 10px 0;
    font-size: 1.25rem;
    line-height: 2rem;
    font-weight: 500;
	color:#ea5158;
  }
</style>

<svelte:head>
  <title>Red Flaglink</title>
</svelte:head>

<ul>
  {#each posts as post}
    <a href={post.link}>
      <li>
        <div class="cmpname">{post.title}</div>
        {post.slug}
      </li>
    </a>
  {/each}
</ul>
