<script>
	import { onMount } from 'svelte'
	import axios from 'axios'
	import { api } from '../api.config.js'
	import { Link } from 'svelte-routing'
	import Icon from 'fa-svelte'
	import { faSpinner } from '@fortawesome/free-solid-svg-icons'

	let users = []
	let getUsers = async () => {
		return await axios.get(api.base).then(res => {
			users = res.data
		}).catch(err => {
			console.log(err)
		})
	}

	onMount(getUsers);

</script>

<h2>Users list</h2>

{#if users.length > 0}
	<ul class="list-group">
		{#each users as user}
			<li class="list-group-item d-flex align-items-center" id="{user.id}">
				<div class="rounded-circle">
					<img 
						src="../assets/img/avatar.png"
						alt="{user.username}"
						class="img-fluid rounded-circle"
						width="100"
					/>
				</div>
				<div class="mx-2">
					<h5>
						<Link to="/user/{user.id}">
							{ user.name }
						</Link>
					</h5>
					<h6>@{ user.username }</h6>
				</div>
			</li>
		{/each}
	</ul>
{:else}
	<span class="h4">
		<Icon icon={faSpinner} class="fa-spine mx-2" />
		 loading...
	</span>
{/if}
