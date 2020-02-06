<script>
	import { onMount } from 'svelte'
	import axios from 'axios'
	import { api } from '../api.config.js'

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
						class="img-fluid"
						width="100"
					/>
				</div>
				<div class="mx-2">
					<h5>
						<a href="{api.base}/{user.id}" class="btn-link">
							{ user.name }
						</a>
					</h5>
					<h6>@{ user.username }</h6>
				</div>
			</li>
		{/each}
	</ul>
{:else}
	<span class="h4">no data</span>
{/if}
