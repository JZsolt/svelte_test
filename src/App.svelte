<script>
    export let name;
    // export let age;
    export let newName;
    let color = 'Zold'
    const test = () => {
        newName = 'Adel'
        color = 'Keke'
    };
    // const testFunc = (e) => {
    //     color = e.target.value
    // }
    let peoples = [
        {name: 'Zsolt', color: 'blue', age: 21, id: 1},
        {name: 'Adel', color: 'red', age: 12, id: 2},
        {name: 'Pista', color: 'green', age: 5, id: 3}
    ];

    const deleteF = (id) => {
        console.log(id)
        peoples = peoples.filter((people) => people.id != id)
        console.log(peoples)
    }
    const  addPeople = () => {
        peoples = peoples.push({
            name: 'Random',
            color: 'grey',
            age: 777,
            id: 5
        })
        console.log(peoples)
    }
</script>

<main>
    <h1>Hello {name}!</h1>
    <p on:click={test}> My name is {newName}!</p>
    <p>{color}</p>
    <p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
    <!--    <input type="text" on:input={testFunc} value="{color}">-->
    <input type="text" bind:value={color}>
    {#each peoples as item}
        <div>
            <h4 style="display: inline-block; color: {item.color}"><span style="font-weight: bold">{item.id}
                . </span>{item.name}</h4>
            <p style="display: inline-block">Is {item.age}!</p>
            <button on:click={() => {deleteF(item.id)}}>Delete</button>
        </div>
    {:else }
        Nincs ember akit kiirjak
        <button on:click={addPeople}>ADD</button>
    {/each}
</main>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }

    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>