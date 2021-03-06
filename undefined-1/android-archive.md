# Android Archive로 부터 설치하기

AAR\(Android Archive\)는 Android 라이브러리 모듈로써 어플리케이션에 포함되어 빌드되기 위한 일련의 정보를 포함하고 있다. 인증 모듈을 사용해서 개발을 진행하기 위해서는 Android Studio에서 AAR을 종속성에 추가해야 한다.

## AAR 파일 가져오기

AAR 파일은 다음의 url로 부터 얻을 수 있다.

```text
https://blocko.blob.core.windows.net/coinstack/coinstack-fingerprint-1.0.0.aar
```

##  AAR 종속성에 추가하기

Android Studio에서 "File &gt; New Module..."을 선택한다.

![](../.gitbook/assets/import-module-step1.jpg)

"Import .JAR / .AAR Package"를 선택한다.

![](../.gitbook/assets/import-module-step2.png)

파일의 경로를 입력한다.

![](../.gitbook/assets/import-module-step3.png)

입력칸 우측에 버튼을 누르면 선택 대화창을 이용할 수 있다.

![](../.gitbook/assets/import-module-step4.png)

선택된 경로가 정상적으로 입력되었는지 확인한다.

![](../.gitbook/assets/import-module-step5.png)

종료 버튼을 누르고,프로젝트에 해당 모듈이 정상적으로 포함되었는지 확인한다.

![](../.gitbook/assets/import-module-step6.png)

