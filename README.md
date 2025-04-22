<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Chair to Sit Means More</title>
    <style>
      html,
      body {
        margin: 0;
        padding: 0;
        width: 100%;
        height: 100%;
        background: #000;
        font-family: sans-serif;
        overflow: hidden;
      }

      .container {
        position: relative;
        width: 100vw;
        height: 100vh;
      }

      .page {
        position: absolute;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
        transition: opacity 0.8s ease;
      }

      .hidden {
        opacity: 0;
        pointer-events: none;
      }

      .page1 {
        background: url("https://i.imgur.com/2vfTPLy.png") no-repeat center center;
        background-size: cover;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        z-index: 2;
      }

      .title-img {
        max-width: 70%;
        z-index: 3;
      }

      .click-area {
        position: absolute;
        inset: 0;
        cursor: pointer;
        z-index: 4;
      }

      .split-left,
      .split-right {
        position: absolute;
        top: 0;
        width: 50%;
        height: 100%;
        background: #fff;
        z-index: 3;
        transition: transform 0.8s ease;
      }

      .split-left {
        left: 0;
        transform: translateX(0);
      }

      .split-right {
        right: 0;
        transform: translateX(0);
      }

      .split-left.animate {
        transform: translateX(-100%);
      }

      .split-right.animate {
        transform: translateX(100%);
      }

      .page2 {
        background: #000;
        color: #fff;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        z-index: 1;
      }

      .page2 img {
        max-width: 60%;
        margin: 20px 0;
        opacity: 0;
        animation: fadeIn 1s forwards;
      }

      .page2 img:nth-child(2) {
        animation-delay: 0.6s;
      }

      @keyframes fadeIn {
        from {
          opacity: 0;
        }
        to {
          opacity: 1;
        }
      }
    </style>
  </head>
  <body>
    <div class="container">
      <!-- 메인 페이지 1 -->
      <div class="page page1" id="page1">
        <img
          src="https://i.imgur.com/54shp1X.png"
          alt="Chair Title"
          class="title-img"
        />
        <div class="click-area"></div>
        <div class="split-left" id="splitLeft"></div>
        <div class="split-right" id="splitRight"></div>
      </div>

      <!-- 메인 페이지 2 -->
      <div class="page page2 hidden" id="page2">
        <img src="https://i.imgur.com/LtWQ1te.png" alt="Sit Means More Title" />
        <img src="https://i.imgur.com/3qg6VjK.png" alt="Description" />
      </div>
    </div>

    <script>
      document.addEventListener("DOMContentLoaded", () => {
        const clickArea = document.querySelector(".click-area");
        const splitLeft = document.getElementById("splitLeft");
        const splitRight = document.getElementById("splitRight");
        const page1 = document.getElementById("page1");
        const page2 = document.getElementById("page2");

        clickArea.addEventListener("click", () => {
          splitLeft.classList.add("animate");
          splitRight.classList.add("animate");

          setTimeout(() => {
            page1.classList.add("hidden");
            page2.classList.remove("hidden");
          }, 800);
        });
      });
    </script>
  </body>
</html>
