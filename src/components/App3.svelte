
<script>
    import Loader from './Loader.svelte'
    import Modal from './Modal.svelte'
    let isOpenModal = false;

    function openModal() {
        isOpenModal = true;
    }

    function closeModal() {
        isOpenModal = false;
    }

    let loading = true
    setTimeout(() => {
        loading = false
    }, 1500);
</script>

{#if loading}
    <Loader scale="2" fixed/>
{:else}
<div class='container'>
    <div on:click={openModal} class="box">모달 열기</div>
        <Modal isOpenModal={isOpenModal} on:closeModal={closeModal} />
        <div class="box">텍스트</div>
    </div>

    <div class='container'>
        <div class="box2">텍스트</div>
        <div class="box2">텍스트</div>
    </div>
{/if}


<style lang="scss">
    .container {
        height: 600px;
    }
    div.box {
        width: 100px;
        height: 100px;
        background-color: antiquewhite;
        margin: 20px;
        border: 5px solid transparent;
        &:hover{
            border: 5px solid black;
            // box-sizing: content-box;
        }
    }

    div.box2 {
        position: relative;
        width: 100px;
        height: 100px;
        background-color: antiquewhite;
        margin: 20px;
        &:hover{
            &::after {
                content: '';
                width: 100%;
                height: 100%;
                position: absolute;
                border: 5px solid red;
                top: 0;
                left: 0;
                box-sizing: border-box;
            }
        }
    }

</style>