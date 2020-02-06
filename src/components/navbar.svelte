<script>
  import {
    Collapse,
    Navbar,
    NavbarToggler,
    NavbarBrand,
    Nav,
    NavItem,
    NavLink,
    UncontrolledDropdown,
    DropdownToggle,
    DropdownMenu,
    DropdownItem
  } from 'sveltestrap';
	import Icon from 'fa-svelte'
	import { faBars, faHome, faInfoCircle } from '@fortawesome/free-solid-svg-icons'
	import { Router, Link } from 'svelte-routing'

  let isOpen = false;

  function handleUpdate(event) {
    isOpen = event.detail.isOpen;
	}

</script>

<Router>
	<Navbar color="primary" dark expand="md">
		<NavbarBrand href="/">sveltestrap</NavbarBrand>
		<NavbarToggler on:click={() => isOpen = !isOpen}>
			<Icon icon={faBars} />
		</NavbarToggler>
		<Collapse {isOpen} navbar expand="md" on:update={handleUpdate}>
			<Nav class="ml-auto" navbar>
				<NavItem>
					<Link class="nav-link" to="/">
						<Icon icon={faHome}></Icon>
						Home
					</Link>
				</NavItem>
				<NavItem>
					<Link class="nav-link" to="/about">
						<Icon icon={faInfoCircle}></Icon>
						About
					</Link>
				</NavItem>
			</Nav>
		</Collapse>
	</Navbar>
</Router>