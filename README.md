# roadedu-skip
로드에듀 교육 스킵 스크립트 공유

더 좋은 방법이 분명 있을텐데 JS를 깊이 있게 다뤄본 적은 없다보니 아쉬운 대로 그냥 이렇게 썼음

우클릭이 안 되게끔 되어있는데, 첫 번째 라인의 playbackrate를 조절해서 원하는 배속으로 조절 가능 </br>
※ playbackrate range : (0.0625 ~ 16)

현재 시간과 </br>
![0404_1](https://github.com/dongsikchoi/roadedu-skip/assets/52738769/bed6ab3f-e318-460d-a457-8d0694221b4e)

종료 시간이 </br>
![0404_2](https://github.com/dongsikchoi/roadedu-skip/assets/52738769/e1ca6eb5-93a3-440a-adde-78c530263040)

동일할 경우  </br>
![0404_3](https://github.com/dongsikchoi/roadedu-skip/assets/52738769/e5d735c6-a49b-4d3e-84ee-d59bff3ff7f7)
</br>
next로 넘어가는 간단한 스크립트임 
(2024.04 기준으로 작성 되었으며, 혹시 안 되면 위 사진과 클래스명이 동일한지 체크해보자. )

- 주의사항
  - **15분** 을 무조건 넘겨야 하므로 강의 목록에서 시간을 보면서 15분이 될 때까지 가만히 **대기**
    
```javascript
document.querySelector('video').playbackRate = 16 // 배속 << 

auto = function checkAndClick() {
    console.log('....'); 

    var currentTimeElement = document.querySelector('.vjs-current-time-display');
    var durationElement = document.querySelector('.vjs-duration-display');

    var currentTimeText = currentTimeElement.innerText;
    var durationText = durationElement.innerText;

    if (currentTimeText === durationText) {
        var nextButton = document.querySelector('.vjs-control.vjs-button[title="Next"]');
        nextButton.click();
        console.log('Next');
    }
    

}

tid = setInterval(auto, 1000);
```

태그가 다른 버전 / durationText가 /0:22 이런 식으로 나와서 split 추가</br>
![image](https://github.com/dongsikchoi/pynecone/assets/52738769/9d9eedfc-0bb7-4714-bf06-18497ed674d3)
```
document.querySelector('video').playbackRate = 16; // 배속

auto = function checkAndClick() {
    console.log('진행중....'); 

    var currentTimeElement = document.querySelector('.time1 .playerText');
    var durationElement = document.querySelector('.time2 .playerText');

    var currentTimeText = currentTimeElement.innerText;
    var durationText = durationElement.innerText.split('/')[1].trim();

    if (currentTimeText === durationText) {
        var nextButton = document.querySelector('._nextBtn');
        nextButton.click();
        console.log('Next');
    }
}

tid = setInterval(auto, 1000);
```
