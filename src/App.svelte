<script>
    import Modal from './Modal.svelte'
    import Form from './AddPersonForm.svelte'

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

    let showModal = false;

    const toggleModal = () => {
        showModal = !showModal;
    }
    const addPerson = (e) => {
        console.log(e.detail)
        peoples = [e.detail, ...peoples];
        showModal = false
    }
</script>

<Modal message="Hello pop vagyok" isPromo={false} showModal="{showModal}" on:click={toggleModal}>
    <h2>Adj hozza uj embert</h2>
    <Form on:addPerson={addPerson}/>
</Modal>

<main>
    <button on:click={toggleModal}>Modal</button>
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
            {#if item.skills}
                <br>
                {#each item.skills as skill}
                    {skill}
                {/each}
            {/if}
            <button on:click={() => {deleteF(item.id)}}>Delete</button>
        </div>
    {:else }
        Nincs ember akit kiirjak
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