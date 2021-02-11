<script>
    import {Button, Input} from '../components'

    export let userbase
    export let user
    export let initPromise
    export let pagina

    let username, password

    function signIn() {
        initPromise = userbase.signIn({username, password})
            .then((u) => user = u)
    }
</script>

<form on:submit|preventDefault={signIn} class="lg:w-2/6 md:w-1/2 bg-gray-100 rounded-lg p-8 flex flex-col mx-auto w-full mt-10 md:mt-0">
    <div class="flex justify-between">
        <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Sign In</h2>
        <Button on:click={() => pagina = 'signup'}>O registrarte</Button>
    </div>
    <Input label="Username" bind:value={username} type="text" required />
    <Input label="Password" bind:value={password} type="password" required />
    <Button>Iniciar Sesion!</Button>
    <!-- <p class="text-xs text-gray-500 mt-3">Literally you probably haven't heard of them jean shorts.</p> -->
</form>