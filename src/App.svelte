<script lang="ts">
  import UuidGenerator from './tools/generators/UuidGenerator.svelte'
  import {Pane, Splitpanes} from "svelte-splitpanes";
  import {Link, Route, Router} from "svelte-routing";
  export let url = ""
</script>

<main>
  <Router {url}>
  <Splitpanes>
    <Pane size={10}>
      <div id="side-bar">
      <h2>Tools List</h2>
      <ul id="tools">
        <li>
          <div>
            <span><img src=""></span>
          <Link to="/uuid4">UUID 4 Generator</Link>
          </div>
        </li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
        <li><Link to="/uuid4">UUID 4 Generator</Link></li>
      </ul>
      </div>
    </Pane>
    <Pane size={90}>
      <div id="main-section">
        <Route path="/uuid4" component={UuidGenerator} />
      </div>
    </Pane>
  </Splitpanes>
  </Router>
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
  #tools {
    list-style: none;
    padding: 0;
  }
</style>