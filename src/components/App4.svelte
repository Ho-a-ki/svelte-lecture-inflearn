
<script>
    import Modal2 from './Modal2.svelte';
    let showModal = false;
    
const toggleModal = () => {
showModal = !showModal;
};

</script>


<Modal2 message='I am a prop value' {showModal} />
    
<button on:click={toggleModal}>Open Modal</button>


<Modal2 {showModal} on:click={toggleModal}>
    <form>
        <input type="text" placeholder="name" />
        <input type="text" placeholder="hair color" />
        <button>Add Person</button>
    </form>
    <div slot="title">
        <h3>Add a new person</h3>
    </div>
</Modal2>
    