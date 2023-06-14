<script>
    let name = '';
    let sum = '';
    let list = [];
    function add() {
        if (name !== '' && sum !== '') {
            list = [
                ...list,
                {
                    Name: name,
                    Sum: Number(sum),
                    Completed: false
                },    
            ]
            name = '';
            sum = '';
        }   
    }

    function remove(index) {
        list.splice(index, 1);
        list = list;
    }

</script>

<h1>Учёт расходов</h1>
<main>
    <form on:submit|preventDefault={add}>
        <div>
            <p>Название:</p>
            <input bind:value={name}> 
            <p>Сумма:</p>
            <input bind:value={sum}>
        </div>           
        <button onclick={add}><span>Добавить</span></button>    
    </form>
    <div class="fill_field">
        
        <div class="row" style="background-color: rgb(168, 168, 168);">
            <div class="column">
                <span><strong>Название</strong></span>
            </div>
            <div class="column">
                <span><strong>Сумма</strong></span>
            </div>
            <div class="column" style="width: 32%;">
                <span><strong>Действия</strong></span>
            </div>
        </div>

        {#each list as item, index}        
            <div class="row" class:completed={item.completed}>
                <div class="column">
                    <span>{item.Name}</span>
                </div>
                <div class="column">
                    <span>{item.Sum}</span>
                </div>
                <div class="column" style="width: 32%;">
                    <button on:click={() => remove(index)}>Удалить</button>
                </div>           
            </div>
        {/each}
    </div>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        min-height: 100%;
        padding: 1vmin;
        box-sizing: border-box;
        font-family: sans-serif;
    }
    
    form {
        width: 100%;
        max-width: 500px;
        display: flex;
        /* align-items: center; */
        margin-bottom: 1rem;
        flex-direction: row;
        /* background-color: aqua; */
        height: 10%;
        align-items: end;
    }
    input {
        flex-grow: 1;
        width: 0;
        border: 1px solid rgb(214, 212, 212);
        box-shadow: none;
        font-size: 1rem;
        margin: 0;
        outline: none;
        width: 200px;
        border-radius:5px;
        margin-right: 20px;
    }
    .fill_field {
        width: 100%;
        max-width: 500px;
    }
    .row {
        /* border: 1px solid black; */
        display: flex;
        /* padding: 20px; */
        /* border-radius: 20px; */
        /* box-shadow: 0 0 15px rgb(0 0 0 /20%); */
        /* background-color: hsla(0, 0%, 100%, 0.2); */
        /* margin-top: 1rem; */
        font-size: 1.2rem;
        /* justify-content: space-between; */
    }
    .column {
        /* vertical-align: middle; */
        border: 1px solid rgb(190, 190, 190);
        width: 34%;
        margin: 0 0 0 0;
        padding: 0 0 0 0;
        height: auto;
        padding: 10px 10px;
        /* padding-top: 13px; */
        /* padding: ; */
    }
    h1 {
        text-align: center;
        font-size: 1.5rem;
        /* margin: 2em  0; */
    }
    button {
        width: 90px;
        border-radius: 5px;
        border: none;
        background-color: rgb(95, 185, 95);
        font-size: 0.8rem;
        color: white;
        padding: 3px;
    }
</style>