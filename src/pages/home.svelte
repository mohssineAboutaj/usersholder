<script>
	import Users from '../components/users.svelte'
</script>

<div class="home">
	<header class="card mt-4 mb-2 font-wight-bold text-center text-capitalize">
		<div class="card-body">
			<h1 class="mt-4 mb-2">
				UsersHolder App
			</h1>
			<h4 class="mb-2">
				a simple app to fetch & print users in cards fetched from <a href="https://jsonplaceholder.typicode.com" class="btn btn-link text-uppercase">jsonplaceholder api</a>
			</h4>
		</div>
	</header>
	<Users />
</div>