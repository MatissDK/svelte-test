<script lang="ts">
    import "../app.css";
    import {page} from '$app/stores';
    import Loader from "$lib/common/Loader.svelte";
    let displayLoader = true;
</script>

{#if displayLoader}
    <Loader on:display={() => displayLoader = false}/>
{/if}
<div class="drawer">
    <input id="my-drawer-3" type="checkbox" class="drawer-toggle"/>
    <div class="drawer-content flex flex-col drop-shadow-md">
        <!-- Navbar -->
        <div class="w-full navbar bg-base-200">
            <div class="flex-none lg:hidden">
                <label for="my-drawer-3" class="btn btn-square btn-ghost">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                         class="inline-block w-6 h-6 stroke-current">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                              d="M4 6h16M4 12h16M4 18h16"></path>
                    </svg>
                </label>
            </div>
            <div class="flex-1 px-2 mx-2">
                <a href="/">PEEPIO</a>
            </div>
            <div class="flex-none hidden lg:block">
                <ul class="menu menu-horizontal">
                    <!-- Navbar menu content here -->

                    <a href="/"
                       class="btn btn-ghost mr-2 {$page.route.id === '/' ? 'bg-base-300' : '' }">
                        Home
                    </a>

                    <a on:click={() => displayLoader = true}
                       href="/about"
                       class="btn btn-ghost  {$page.route.id === '/about' ? 'bg-base-300' : '' }">
                        Login
                    </a>
                </ul>
            </div>
            <div class="avatar online mx-3">
                <div class="w-8 rounded-full ring ring-primary ring-offset-base-100 ring-offset-2">
                    <img src="https://placeimg.com/192/192/people" />
                </div>
            </div>
        </div>
        <!-- Page content here -->
        <slot/>
    </div>
    <div class="drawer-side">
        <label for="my-drawer-3" class="drawer-overlay"></label>
        <ul class="menu p-4 w-80 bg-base-100">
            <a href="/" class="btn btn-ghost w-full mb-2 {$page.route.id === '/' ? 'bg-base-300' : '' }">
                Home
            </a>

            <a href="/about" class="btn btn-ghost w-full {$page.route.id === '/about' ? 'bg-base-300' : '' }">
                About
            </a>
        </ul>

    </div>
</div>