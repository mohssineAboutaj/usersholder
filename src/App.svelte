<script>
	import Navbar from './components/navbar.svelte'
	import Home from './pages/home.svelte'
	import { Router, Route } from 'svelte-routing'

</script>

<Navbar />
<div class="container">
	<Router url="">
		<Route path="/">
			<Home />
		</Route>
		<Route path="/about">
			about
		</Route>
	</Router>
</div>
