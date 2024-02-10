<script lang="ts">
  import UuidGenerator from './tools/generators/UuidGenerator.svelte'
  import {Pane, Splitpanes} from "svelte-splitpanes";
  import {Link, Route, Router} from "svelte-routing";
  export let url = ""
</script>

<main>
  <Router {url}>
  <Splitpanes>
    <Pane minSize={10}>
      <h2>Tools List</h2>
      <ul>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
      </ul>
    </Pane>
    <Pane minSize={10}>
      <Route path="/uuid4" component={UuidGenerator} />
    </Pane>
  </Splitpanes>
  </Router>
</main>

<style>

</style>