<template>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <div class="wrapper">
    <form class="form">
      <div class="pageTitle title"><i class="fa-solid fa-burger"></i>CONTECT US </div>
      <div class="secondaryTitle title">I'm not robot.</div>
      <input type="text" class="name formEntry" placeholder="Name" />
      <input type="text" class="email formEntry" placeholder="Email" />
      <textarea class="message formEntry" placeholder="Message"></textarea>
      <input type="checkbox" class="termsConditions" value="Term">
      <label style="color: grey" for="terms"> I Accept the <span style="color: red">Terms of Use</span> & <span
          style="color: red">Privacy Policy</span>.</label><br>
      <br>
      <button type="submit"
        class="flex w-full justify-center rounded-md bg-indigo-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Submit</button>
    </form>

    <div class="about-tab">
      <!-- Facebook -->

      <a href="https://www.facebook.com" target="_blank" rel="noopener noreferrer" class="social-media-link">
        <button class="social-media-button facebook">
          <i class="fab fa-facebook"></i>
          <p>Facebook</p>
        </button>
      </a>
      <!-- Telegram -->
      <a href="https://telegram.org" target="_blank" rel="noopener noreferrer" class="social-media-link">
        <button class="social-media-button telegram">
          <i class="fab fa-telegram"></i>
          <p>Telegram</p>
        </button>
      </a>
      <!-- TikTok -->
      <a href="https://www.tiktok.com" target="_blank" rel="noopener noreferrer" class="social-media-link">
        <button class="social-media-button tiktok">
          <i class="fab fa-tiktok"></i>
          <p>TikTok</p>
        </button>
      </a>
      <!-- YouTube -->
      <a href="https://www.youtube.com" target="_blank" rel="noopener noreferrer" class="social-media-link">
        <button class="social-media-button youtube">
          <i class="fab fa-youtube"></i>
          <p>YouTube</p>
        </button>
      </a>
      <!-- Line -->
      <a href="https://line.me" target="_blank" rel="noopener noreferrer" class="social-media-link">
        <button class="social-media-button line">
          <i class="fab fa-line"></i>
          <p>Line</p>
        </button>
      </a>
      <!-- Twitter -->
      <a href="https://twitter.com" target="_blank" rel="noopener noreferrer" class="social-media-link">
        <button class="social-media-button twitter">
          <i class="fab fa-twitter"></i>
          <p>Twitter</p>
        </button>
      </a>
    </div>


  </div>
</template>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}

.bradcam_area {
  background-size: cover;
  background-position: center center;
  text-align: center;
  padding: 215px 0 100px 0;
}

.breadcam_bg {
  background-image: url(../image/contactbuger.jpg);

}

.overlay1 {
  position: relative;
  z-index: 0;
}

*,
::after,
::before {
  box-sizing: border-box;
}

#menu div {
  display: block;
  color: var(--bg-color);
  font-size: 30px;
}

/* signup */
#title-Tag-Line {
  font-size: 20px;
}


.wrapper {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 70px;
  padding: 0px 60px 60px 60px;

}

/* form animation starts */
.form {
  background: #fff;
  background-color: rgb(255, 255, 255);
  box-shadow: 0 30px 60px 0 rgba(90, 116, 148, 0.4);
  border-radius: 5px;
  /* max-width: 480px; */
  width: 700px;
  /* margin-left: auto;
    margin-right: auto; */
  padding-top: 5px;
  padding-bottom: 5px;
  left: 0;
  right: 0;
  /* position: absolute; */
  border-top: 5px solid var(--second-color);
  /*   z-index: 1; */
  animation: bounce 2.5s infinite;
}

::-webkit-input-placeholder {
  font-size: 1.3em;
}

.title {
  display: block;
  font-family: sans-serif;
  margin-left: 10px;
  width: 300px;
  padding: 20px;
}

.termsConditions {
  margin: 0 auto 5px 80px;
  padding: 20px;
}

.pageTitle {
  font-size: 2em;
  font-weight: bold;
}

.secondaryTitle {
  color: grey;
}

.name {
  background-color: #ebebeb;
  color: black;
  width: 600px;
}

.name:hover {
  border-bottom: 5px solid var(--second-color);
  height: 40px;
  width: 550px;
  transition: ease 1s;
}

.email {
  background-color: #ebebeb;
  /* height: 2em; */
  width: 600px;
}

.email:hover {
  border-bottom: 5px solid var(--second-color);
  height: 40px;
  width: 550px;
  transition: ease 1s;
}

.message {
  background-color: #ebebeb;
  overflow: hidden;
  height: 10rem;
  width: 600px;
}

.message:hover {
  border-bottom: 5px solid var(--second-color);
  height: 10em;
  width: 550px;
  transition: ease 1s;
}

.formEntry {
  display: block;
  margin: 30px auto;
  min-width: 300px;
  padding: 10px;
  border-radius: 2px;
  border: none;
  transition: all 0.5s ease 0s;
}

.submit {
  width: 200px;
  color: white;
  background-color: var(--second-color);
  font-size: 20px;
}

.submit:hover {
  box-shadow: 15px 15px 15px 5px rgba(78, 72, 77, 0.219);
  transform: translateY(-3px);
  width: 300px;
  border-top: 5px solid black;
  border-radius: 0%;
}

@keyframes bounce {
  0% {
    tranform: translate(0, 3px);
  }

  50% {
    transform: translate(0, 8px);
  }
}

.about-tab {
  padding: 30px;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  /* Align items to the right */
  margin-left: 10px;
}

.social-media-button {
  display: inline-block;
  margin: 10px;
  padding: 20px;
  border: none;
  border-radius: 10px;
  width: 120px;
  text-align: center;
  background-color: transparent;
  cursor: pointer;
  transition: all 0.3s ease;
}

.social-media-button i {
  font-size: 40px;
  margin-bottom: 10px;
}

.social-media-button p {
  font-size: 16px;
}

.social-media-button:hover {
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
  transform: translateY(-3px);
}

.social-media-button.facebook {
  background-color: #3b5998;
  color: #fff;
}

.social-media-button.telegram {
  background-color: #0088cc;
  color: #fff;
}

.social-media-button.tiktok {
  background-color: #000;
  color: #fff;
}

.social-media-button.youtube {
  background-color: #ff0000;
  color: #fff;
}

.social-media-button.line {
  background-color: #00b900;
  color: #fff;
}

.social-media-button.twitter {
  background-color: #1da1f2;
  color: #fff;
}
/* For smaller screens */
@media (max-width: 768px) {
  .wrapper {
    padding: 20px;
  }

  .form {
    width: 100%;
    padding: 20px;
  }

  .name,
  .email,
  .message {
    width: 100%;
  }

  .about-tab {
    flex-direction: column;
    align-items: center;
    margin-left: 0;
  }
}

/* For medium-sized screens */
@media (min-width: 769px) and (max-width: 1024px) {
  .wrapper {
    gap: 50px;
  }

  .form {
    width: 60%;
    padding: 30px;
  }
}

/* For larger screens */
@media (min-width: 1025px) {
  .wrapper {
    gap: 70px;
  }

  .form {
    width: 700px;
    padding: 60px;
  }
}


</style>