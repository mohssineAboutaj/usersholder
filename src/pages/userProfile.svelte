<script context="module">
	export function preload(page) {
		let id = page.params.id;
		return { id };
	}
</script>

<script>
	import { onMount } from 'svelte'
	import axios from 'axios'
	import { api } from '../api.config.js'
	import Icon from 'fa-svelte'
	import {
		faUserCircle, 
		faAt, 
		faGlobe, 
		faPhone, 
		faMapMarkerAlt, 
		faBriefcase, 
	} from '@fortawesome/free-solid-svg-icons'

	export let user = {}

	export let id;

	onMount(() => {
		axios.get(api.base + '/' + id).then(res => {
			user = {...res.data.data, ...res.data.ad }
		}).catch(err => {
			console.log(err)
		})
	});

</script>

<h3 class="text-center text-capitalize mt-2 mb-4">profile</h3>

{#if user}
	<div class="card mx-auto" style="max-width: 500px">
		<div class="text-center">
			<img 
				src="{ user.avatar }"
				alt="{ user.first_name }"
				class="img-fluid rounded-circle"
				width="100"
			/>
		</div>
		<div class="card-body">
			<h1 class="card-title h3 text-capitalize text-center">
				{ `${user.first_name} ${user.last_name} ` }
			</h1>
		</div>
		<div>
			<ul class="list-group">
				<li class="list-group-item d-flex align-items-center">
					<span class="badge badge-pill">
						<Icon icon={faUserCircle} />
					</span>
					{ user.first_name }
				</li>
				<li class="list-group-item d-flex align-items-center">
					<span class="badge badge-pill">
						<Icon icon={faAt} />
					</span>
					{ user.email }
				</li>
				<li class="list-group-item d-flex align-items-center">
					<span class="badge badge-pill">
						<Icon icon={faBriefcase} />
					</span>
					{ user.company }
				</li>
				<li class="list-group-item d-flex align-items-center">
					<span class="badge badge-pill">
						<Icon icon={faPhone} />
					</span>
					+123456789
				</li>
				<li class="list-group-item d-flex align-items-center">
					<span class="badge badge-pill">
						<Icon icon={faGlobe} />
					</span>
					{ user.url }
				</li>
			</ul>
		</div>
	</div>
{:else}
	<span class="h4">
		404 not found
	</span>
{/if}