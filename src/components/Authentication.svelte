<script>
    let email = "";
    let password = "";
    let confPass = "";
    let error = false;
    let register = false;

    function handleAuthentication() {
        if (!email || !password || (register && !password)) {
            error = true;
            return;
        }
    }
    function handleRegister() {
        register = !register;
    }
</script>

<div class="authContainer">
    <form action="">
        <h1>{register ? "Register" : "Login"}</h1>
        {#if error}
            <p class="error">
                The information you have entered is not correct.
            </p>
        {/if}
        <label for="email">
            <p class={email ? "above" : "center"}>Email</p>
            <input bind:value={email} type="email" placeholder="Email" />
        </label>
        <label for="password">
            <p class={password ? "above" : "center"}>Password</p>
            <input
                bind:value={password}
                type="password"
                placeholder="Password"
            />
        </label>
        {#if  register}
            
        <label for="password">
            <p class={confPass ? "above" : "center"}>Confirm Password</p>
            <input
            bind:value={confPass}
            type="password"
            placeholder="Confirm Password"
            />
        </label>
        {/if}
        <button type="button">Submit</button>
    </form>
    <div class="options">
        <p class="">Or</p>
        {#if register}
            <div class="">
                <p class="">Already have an account?</p>
                <p on:click={handleRegister}  on:keydown={()=>{}}>Login</p>
            </div>
        {:else}
            <div class="">
                <p class="">Don't have an account?</p>
                <p on:click={handleRegister}  on:keydown={()=>{}}>Register</p>
            </div>
        {/if}
    </div>
</div>

<style class="">
    .authContainer {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        flex: 1;
        padding: 24px;
    }
    form {
        display: flex;
        flex-direction: column;
        gap: 14px;
    }
    form,
    .options {
        width: 400px;
        max-width: 100%;
        margin: 0 auto;
    }
    form label {
        position: relative;
        border: 1px solid navy;
        border-radius: 10px;
    }
    form label:focus-within {
        color: red;
    }
    form input {
        width: 100%;
        border: none;
        outline: none;
        background: transparent;
        color: black;
        padding: 14px;
    }
    form button {
        background: navy;
        color: white;
        border: none;
        padding: 14px 0px;
        border-radius: 10px;
        cursor: pointer;
        font-size: 1rem;
    }
    form button:hover {
        background: blue;
    }
    h1 {
        text-align: center;
        font-size: 3rem;
    }
    .above,
    .center {
        position: absolute;
        transform: translateY(-50%);
        pointer-events: none;
        color: white;
        border-radius: 8px;
        padding: 0px 6px;
        font-size: 0.8rem;
    }
    .above {
        top: 0;
        left: 24px;
        background: navy;
        border: 1px solid blue;
        font-size: 0.7rem;
    }
    .center {
        top: 50%;
        left: 6px;
        border: 1px solid transparent;
        opacity: 0;
    }
    .error {
        font-size: 0.9rem;
        color: coral;
    }
    .options {
        padding: 14px 0px;
        overflow: hidden;
        font-size: 0.9rem;
        display: flex;
        flex-direction: column;
        gap: 4px;
    }
    .options > p {
        position: relative;
        text-align: center;
        width: fit-content;
        margin: 0 auto;
        padding: 0 8px;
    }
    .options > p::after,
    .options > p::before {
        position: absolute;
        content: "";
        top: 50%;
        transform: translateY(-50%);
        width: 100vw;
        height: 1.5px;
        background: black;
    }
    .options > p::after {
        right: 100%;
    }
    .options > p::before {
        left: 100%;
    }
    .options div{
        display: flex;
        align-items: center;
        gap: 8px;
        justify-content: center;
    }
    .options div p:last-of-type{
        color: blue;
        cursor: pointer;
    }
</style>
