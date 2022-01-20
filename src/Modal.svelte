<script>
    let showModal = true;
    let isPromo = false
</script>

{#if showModal}
    <div class="backdrop" class:promo={isPromo}>
        <div class="modal">
            <p>TEST</p>
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
</style>