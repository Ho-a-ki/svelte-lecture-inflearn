<!-- src/Modal.svelte -->
<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    export let isOpenModal;
    function closeModal() {
        isOpenModal = false;
        dispatch('closeModal', { isOpenModal });
    }
</script>

<div id="background" style="--display: {isOpenModal ? 'block' : 'none'};" on:click={closeModal}></div>
<div id="modal" style="--display: {isOpenModal ? 'block' : 'none'};">
    <div class="modal">
      <span>화이팅!!♥♥♥</span>
       당신의 꿈을 응원합니다.
      <img src="/images/licat.png" alt="">
      <button on:click={closeModal} >종료하고 진짜 훈련하러 가기 GO! GO!</button>
      <small>(그냥 닫기 버튼입니다.)</small>
    </div>
  </div>


<style lang="scss">
    $color-primary : #FCEE21;
    $color-purple : #662D91;
    @font-face {
    font-family: 'OTEnjoystoriesBA';
    src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_two@1.0/OTEnjoystoriesBA.woff') format('woff');
    font-weight: normal;
    font-style: normal;
    }

    #background {
        display: var(--display);
        position: fixed;
        z-index: 1;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
    }

    #modal {
        display: var(--display);
       	position: fixed;
        z-index: 2;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background: #fff;
        filter: drop-shadow(0 0 20px #333);
        border-radius: 20px;
    }


    .modal {
        font-family: 'OTEnjoystoriesBA';
        display: flex;
        flex-direction: column;
        color: $color-purple;
        align-items: center;
        justify-content: center;
        width: 600px;
        height: 600px;
        border-radius: 20px;
        font-size: 24px;
        span {
            font-size: 70px;
        }

        button {
            font-size: 24px;
            border: none;
            cursor: pointer;
            margin: 20px 0;
            padding: 20px 40px;
            background: $color-primary;
            color: $color-purple;
            border-radius: 56px;
            font-family: 'Gmarket Sans';
            font-weight: 800;
            box-shadow: 0px 6px 16px 0px rgb(0 0 0 / 15%), 0px 5px 16px 0px rgb(0 0 0 / 15%);
        }

        small {
            font-family: 'Gmarket Sans';
            font-size: 16px;
        }
}
</style>