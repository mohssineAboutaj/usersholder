<script>
	import Navbar from './components/navbar.svelte'
	import Home from './pages/home.svelte'
	import About from './pages/about.svelte'
	import UserProfile from './pages/userProfile.svelte'
	import { Router, Route } from 'svelte-routing'

</script>

<Navbar />
<div class="container">
	<Router url="">
		<Route path="/">
			<Home />
		</Route>
		<Route path="/about">
			<About />
		</Route>
		<Route path="/user/:id" let:params>
			<UserProfile id={params.id} />
		</Route>
	</Router>
</div>
