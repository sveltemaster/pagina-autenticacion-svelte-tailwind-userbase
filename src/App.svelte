<script>
    import Tailwindcss from './Tailwindcss.svelte'
    import SignUp from './routes/SignUp.svelte'
    import SignIn from './routes/SignIn.svelte'
    import ForgotPassword from './routes/ForgotPassword.svelte'
    import {Button} from './components'

    let user = null

    const userbase = window.userbase
    let initPromise = userbase.init({appId: 'cc34d760-bf44-4aba-8ed6-9e7db48bb9be'})
        .then((session) => user = session.user)
    
    function signOut() {
        initPromise = userbase.signOut()
            .then(() => user = null)
    }

    let pagina = 'signup'
</script>

<Tailwindcss />


<div class="container flex justify-center items-center h-screen w-screen mx-auto">
    {#await initPromise}
        Loading...
    {:then _}
        {#if user}
            Holita, {user.username}!
            <Button on:click={signOut}>Log out</Button>
        {:else}
            {#if pagina === 'signup'}
                <SignUp {userbase} bind:user bind:initPromise bind:pagina />
            {:else if pagina === 'signin'}
                <SignIn {userbase} bind:user bind:initPromise bind:pagina />
            {:else if pagina === 'forgot'}
                <!-- <SignIn {userbase} bind:user bind:initPromise /> -->
            {/if}
        {/if}
    {/await}
</div>
