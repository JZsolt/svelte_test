<script>
    import {createEventDispatcher} from 'svelte';

    let dispatch = createEventDispatcher();
    let name;
    let color;
    let age;
    let skills = [];
    const submitForm = () => {
        const people = {
            name,
            color,
            age,
            skills,
            id: Math.floor(Math.random()*100)
        };
        dispatch('addPerson', people);
    }

</script>

<form on:submit|preventDefault={submitForm}>
    <input type="text" placeholder="name" bind:value={name}>
    <label><strong>Szinek</strong></label>
    <select bind:value={color}>
        <option value="black">black</option>
        <option value="orange">orange</option>
        <option value="blue">blue</option>
    </select>
    <input type="number" placeholder="age" bind:value={age}>
    <label><strong>Skills</strong></label>
    <input type="checkbox" bind:group={skills} value="futas">futas
    <input type="checkbox" bind:group={skills} value="foci">foci
    <input type="checkbox" bind:group={skills} value="valami">valami
    <input type="checkbox" bind:group={skills} value="mas">mas
    <button>Add hozza</button>
</form>

<style>

</style>