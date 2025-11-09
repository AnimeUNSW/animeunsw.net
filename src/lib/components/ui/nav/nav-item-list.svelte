<script>
  import NavItem from "./nav-item.svelte";
  export let scrollY = 0;
</script>

<!-- list of nav items -->
<ul class="flex flex-row space-x-9">
  <NavItem href="/events" label="Events" {scrollY} />
  <NavItem href="/sponsors" label="Sponsors" {scrollY} />
  <NavItem href="/info" label="Info" {scrollY} />
  <NavItem href="/blog" label="Blog" {scrollY} />
</ul>
