<script>
    export let message = 'default CIM';
    export let showModal = false;
    export let isPromo = false;
    const closeModal = () => {
        showModal = false;
    }
</script>

{#if showModal}
    <div class="backdrop" class:promo={isPromo} on:click|self>
        <div class="modal">
            <div class="modal-header">
                <div on:click class="close">x</div>
            </div>
            <p>{message}</p>
        </div>
    </div>
{/if}

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, .8);
    }

    .modal {
        padding: 10px;
        border-radius: 8px;
        background: #f1f1f1;
        max-width: 70%;
        margin: 10% auto;
        text-align: center;
    }
    .promo .modal {
        background: crimson;
        color: white;
    }
    .close {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 30px;
        height: 30px;
        float: right;
        background: #dddddd;
        margin: 10px 10px 0;
        cursor: pointer;
        color: #333333;
        border-radius: 8px;
    }
</style>