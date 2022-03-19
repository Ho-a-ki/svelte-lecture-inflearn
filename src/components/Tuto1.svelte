
<script>
import Modal from './Modal.svelte';
import Loader from './Loader.svelte'

  let isOpenModal = false;

  function openModal() {
      isOpenModal = true;
  }

  function closeModal() {
      isOpenModal = false;
  }


  let profession = ""
  let studyTime = ""
  let loading = false
  let howManyDays = 0
  let submit = false

  function submitFunc() {
    if (profession == "" | studyTime == 0) {
      alert('입력되지 않았습니다.')
      return
    }

    if (studyTime > 24) {
      alert('시간은 24시간 이하여야만 합니다')
      return
    }

    submit = false
    loading = true
    setTimeout(() => {
      submit = !submit
      loading = false
      howManyDays = Math.ceil(10000 / studyTime)
    } , 1500)
  }

  function copyUrl() {
    var dummy = document.createElement('input'),
    text = window.location.href;

    document.body.appendChild(dummy);
    dummy.value = text;
    dummy.select();
    document.execCommand('copy');
    document.body.removeChild(dummy);
    alert('URL이 복사되었습니다.')
  }

</script>


<body>
  <div id="title">
    <div class="background">
      <img src="images/time.svg" alt="">
    </div>
    <img src="images/image.svg" alt="">
  </div>

  <section class="text">
    <h2>"연습은 어제의 당신보다 당신을 더 낫게 만든다"</h2>
  </section>
  <section class="quote">
    <p>
      <span>1만 시간의 법칙</span>은<br> 
      어떤 분야의 전문가가 되기 위해서는 <br>
      최소한 1만 시간의 훈련이 필요하다는 법칙이다.
    </p>
  </section>
  <div class="input-area">
    <p>
      <span>나는</span> 
      <input 
      placeholder="예)프로그래밍"
      type="text" bind:value={profession}> 전문가가 될 것이다.
    </p>
    <p>
      <span>그래서 앞으로 매일 하루에</span>
      <input 
      placeholder="예)5"
      bind:value={studyTime}
      type="number"> 시간 식 훈련할 것이다.
    </p>
  </div>
  <div class="submit-btn">
    <button on:click={submitFunc}>나는 며칠 동안 훈련을 해야 1만 시간이 될까?</button>
    <img src="images/click.png" alt="">
  </div>

  
  
  {#if loading}
  <div id="loading">
    <Loader />
  </div>
  {/if}
  
  {#if submit}
  <div class="result">
    <p>당신은 <span> {profession} </span> 전문가가 되기 위해서</p>
    <p>대략 <span>{howManyDays}</span> 일 이상 훈련하셔야 합니다! :) </p>
  </div>
  <div class="btn-area">
    <button on:click={openModal}>훈련하러 가기 GO! GO!</button>
      <Modal isOpenModal={isOpenModal} on:closeModal={closeModal} />
    <button on:click={copyUrl}>공유하기</button>
  </div>
  {/if}

  <footer>
    <div id="logo"></div>
    <small>※ 본 서비스 내 이미지 및 콘텐츠의 저작권은 주식회사 WeNiv에 있습니다.<br>
      수정 및 재배포, 무단 도용 시 법적인 문제가 발생할 수 있습니다.</small>
  </footer>

</body>


<style lang='scss'>
  @font-face {
	font-family: 'Gmarket Sans';    font-style: normal;    font-weight: 700;
	src: local('Gmarket Sans Bold'), local('GmarketSans-Bold'),
	url('http://script.ebay.co.kr/fonts/GmarketSansBold.woff2') format('woff2'), /* Chrome 26+, Opera 23+, Firefox 39+ */
	url('http://script.ebay.co.kr/fonts/GmarketSansBold.woff') format('woff'); /* Chrome 6+, Firefox 3.6+, IE 9+, Safari 5.1+ */
}
@font-face {
	font-family: 'Gmarket Sans';    font-style: normal;    font-weight: 500;
	src: local('Gmarket Sans Medium'), local('GmarketSans-Medium'),
	url('http://script.ebay.co.kr/fonts/GmarketSansMedium.woff2') format('woff2'), /* Chrome 26+, Opera 23+, Firefox 39+ */
	url('http://script.ebay.co.kr/fonts/GmarketSansMedium.woff') format('woff'); /* Chrome 6+, Firefox 3.6+, IE 9+, Safari 5.1+ */
}
@font-face {
	font-family: 'Gmarket Sans';    font-style: normal;    font-weight: 300;
	src: local('Gmarket Sans Light'), local('GmarketSans-Light'),
	url('http://script.ebay.co.kr/fonts/GmarketSansLight.woff2') format('woff2'), /* Chrome 26+, Opera 23+, Firefox 39+ */
	url('http://script.ebay.co.kr/fonts/GmarketSansLight.woff') format('woff'); /* Chrome 6+, Firefox 3.6+, IE 9+, Safari 5.1+ */
}

@font-face {
    font-family: 'OTEnjoystoriesBA';
    src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_two@1.0/OTEnjoystoriesBA.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

  $color-primary : #FCEE21;
  $color-purple : #662D91;
  
  
  body {
    background: $color-purple;
    text-align: center;
    font-family: 'Gmarket Sans';
    font-weight: 300;
  }

  #loading {
    margin-top: 100px;
    margin-bottom: 100px;
  }

  .submit-btn {
    display: flex;
    justify-content: center;
    position: relative;
    img {
      position: relative;
      right: -5px;
      top: 10px
    }
  }


  div#title {
    padding-top: 150px;
    margin-bottom: 150px;
    display: flex;
    position: relative;
    justify-content: center;
    align-items: center;

    .background {
      position: absolute;
      margin: 0 auto;
    }
  }

  section.text {
    color : $color-primary;
    font-family: 'OTEnjoystoriesBA';
    margin-bottom: 78px;
    h2 {
      font-size: 36px;
    }
  }

  .quote {
    color: white;
    margin-bottom: 96px;
    font-size: 18px;
    line-height: 30px;
    p {
      background-image: url(images/quotes.png);
      background-repeat: no-repeat;
      background-position: 50% 40%;
    }
    span {
      font-weight: 700;
      font-family: 'Gmarket Sans';
      font-size: 24px;
    }
  }

  .input-area {
    font-size: 24px;
    color: white;
    margin-bottom: 70px;
    p {
      margin-bottom: 10px;
    }
  }

  input {
    font-family: 'Gmarket Sans';
    width: 228px;
    height: 57px;
    padding: 0 10px;
    text-align: center;
    color: $color-purple;
    background: #FFFFFF;
    border-radius: 7px;
    font-size: 24px;
    margin: 0 10px;
    &::placeholder {
      color: #BABCBE;
    }
  }

  button {
    font-size: 24px;
    padding: 0 40px;
    background: $color-primary;
    color: $color-purple;
    border-radius: 56px;
    font-family: 'Gmarket Sans';
    font-weight: 800;
  }

  .result {
    margin: 120px 0;
    color : white;
    line-height: 24px;
    font-size: 24px;
    p {
      display: flex;
      justify-content: center;
      align-items: center;
      span {
        font-weight: 700;
        margin: 0 10px;
        font-size: 72px;
        line-height: 72px;
      }
    }
  }

  .btn-area {
    position: relative;
    button {
      padding: 20px 40px;
      &:nth-child(2) {
        margin-left: 18px;
        background-color: #FFFFFF;
        width: 191px;
      }
    }
  }

  footer {
    font-weight: 200;
    font-family: 'Pretendard';
    margin-top: 130px;
    color : white;
    padding-bottom: 100px;
  }

</style>