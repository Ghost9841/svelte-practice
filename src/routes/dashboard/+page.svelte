<script>
    let todoList = ["Something","Hello"];
    let currTodo = '';
    let error = false;
    function addTodo() {
        error = false;
       if (!currTodo) {
        error = true;
       }
       todoList = [...todoList, currTodo];
       currTodo= "";
    }
</script>

<div class="mainCointainer">
    <section class="header-cointainer">
        <h1 class="">To Do List</h1>
        <button class="">Save</button>
    </section>

    <main>
        {#each todoList as todo,  index}    
            <div class="todo-display">
                <p class="">{index+1}. {todo}</p>
                <div class="actions">
                    <button>Edit</button>
                    <button>Delete</button>
                </div>
            </div>
        {/each}
    </main>
    <div class="enter-todo" class:errorBorder={error}>
        <input bind:value={currTodo} type="text" placeholder="Enter todo"/>
        <button onclick={addTodo}>Add</button>

    </div>
</div>

<style class="">
    .mainCointainer {
        display:flex;
        flex-direction: column;
        min-height: 100vh;
        gap: 24px;
        padding: 24px;
        width: 100%;
        max-width: 1000px;
        margin: 0 auto;
    }
    .header-cointainer {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .header-cointainer button{
        padding: 10px 24px 10px;
        background: cyan;
        font-weight: 600;
        border: none;
        cursor: pointer;
        border-radius: 10px;
    }
    .enter-todo button{
        padding: 0 14px;
        background: cyan;
        font-weight: 600;
        border: none;
        cursor: pointer;
        border-radius: 10px;
    }
    .enter-todo button:hover{
        background: black;
        color:cyan;
    }
    main{
        display: flex;
        flex-direction: column;
        flex:1;
        gap: 8px;
    }

    .todo-display {
        border-left: 1px solid blue;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 8px 14px;

    }
    .actions{
        display:flex;
        align-items: center;
        gap: 14px;
        font-size:1.3rem;
    }
    .actions button{
        padding: 10px 24px 10px;
        background: cyan;
        font-weight: 600;
        border: none;
        cursor: pointer;
        border-radius: 10px;
    }
    .enter-todo{
        display: flex;
        align-items: stretch;
        border: 1px solid cyan;
        border-radius: 10px;

    }
    .errorBorder { 
        border-color: coral !important;
    }
    .enter-todo input{
        background: transparent;
        border:none;
        padding:14px;
        color:blue;
        flex:1;
    }
    .enter-todo input:focus{
        outline:none;
    }
   
</style>