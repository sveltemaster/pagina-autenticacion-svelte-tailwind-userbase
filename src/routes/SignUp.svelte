<script>
    import {Button, Input} from '../components'

    export let userbase
    export let user
    export let initPromise
    export let pagina

    let username, password, email

    function signUp() {
        initPromise = userbase.signUp({username, password, email})
            .then((u) => user = u)
    }
</script>

<form on:submit|preventDefault={signUp} class="lg:w-2/6 md:w-1/2 bg-gray-100 rounded-lg p-8 flex flex-col mx-auto w-full mt-10 md:mt-0">
    <div class="flex justify-between">
        <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Sign Up</h2>
        <Button on:click={() => pagina = 'signin'}>O iniciar sesion</Button>
    </div>
    
    <Input label="Username" bind:value={username} type="text" required />
    <Input label="Password" bind:value={password} type="password" required />
    <Input label="Email" bind:value={email} type="email" required />
    <Button>Registrarte!</Button>
    <!-- <p class="text-xs text-gray-500 mt-3">Literally you probably haven't heard of them jean shorts.</p> -->
</form>