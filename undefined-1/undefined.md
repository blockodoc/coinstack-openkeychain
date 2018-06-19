# 예제 프로그램 실행해보기

예제 프로그램은 키를 키저장소\(keystore\)에 생성하고 지문인증을 통해 키를 얻어오는 과정을 보여주는 안드로이드 어플리케이션이다. 예제 프로그램 전체는 MIT 라이센스이므로 자유롭게 수정이 가능하며, 필요에 따라 원래 소스에 반영\(pull request\)할 수 있다.

## 예제 프로그램 가져오기

예제 프로그램은 [https://bitbucket.org/cloudwallet/android-fingerprint-keychain](https://bitbucket.org/cloudwallet/android-fingerprint-keychain) 에 호스팅되고 있다. 다음 명령을 통해 간단히 소스를 가져올 수 있다.

```text
git clone https://blocko_bylee@bitbucket.org/cloudwallet/android-fingerprint-keychain.git
```

명령행이 익숙하지 않다면 Android Studio 메뉴에서 "File &gt; New &gt; Project from Version Control &gt; Git"을 사용할 수 있다.

## 예제 프로그램 구성

### 지문 인증 모듈

안드로이드의 키 저장소와 지문 인증 과정을 손쉽게 사용할 수 있도록 API를 제공한다.

### 안드로이드 어플리케이션

지문 인증 모듈을 어떻게 사용하는지 보여주기 위한 예제이다.

## 예제 프로그램 실행

예제 프로그램의 프로젝트에는 junit 테스트 케이스와 android app을 실행할 수 있다. 예제 프로그램을 실행하기 위해서는 대상 프로그램을 app으로 선택하고 실행하면 된다.

## 예제 프로그램 분석

### MainActivity

크게 개인키를 저장소에서 생성하는 부분과 인증을 시작하는 부분으로 나뉜다. 유심히 보아야할 부분은 authenticate 메쏘드이다.

큰 흐름은 mac을 생성\(line2~4\)한 후 인증 절차\(FingerprintAuthenticationProcess\)에 전달\(line28\)하고, 성공하면 해당 mac의 doFinal을 호출\(line17\)할 수 있게 된다. 이때, 인증 절차에서 발생하는 이벤트를 FingerprintAuthenticationCallback가 처리\(line11~24\)하도록 한다. 본 예제에서 FingerprintAuthenticationCallback는 인증 절차에 대한 이벤트와 FragmentDialog에서 발생하는 사용자 이벤트를 모두 처리하도록 구현되어있다.

### FingerprintAuthenticationCallback

FingerprintAuthenticationCallback는 다음의 두 인터페이스를 구현하고 있다. 구현 내용은 간단히 3번의 인증 기회안에 인증을 진행하는 내용이다.

#### FingerprintAuthenticationHandler

인증 절차에서 발생하는 이벤트들을 처리하는 인터페이스이다. 다음의 상황에 따라 해당 메쏘드가 호출된다.

| 상황 | 메쏘드 | 진행 여부 |
| :--- | :--- | :--- |
| 인증 절차 시작 | onStart\( FingerprintAuthenticationProcess process \) | Y |
| 인증 절차 종료 | onEnd\( FingerprintAuthenticationProcess process \) | N |
| 인증 성공 | onSuccess\( FingerprintAuthenticationProcess process \) | N |
| 인증 실패 | onFailure\( FingerprintAuthenticationProcess process, CharSequence help \) | Y |
| 에러 | onError\( FingerprintAuthenticationProcess process, Throwable exception \) | N |

* 진행 여부는 해당 이벤트 이후 계속 지문 인식 상태를 유지하는지 여부이다.

#### FingerprintAuthenticationDialogFragmentListener

FingerprintAuthenticationDialog가 dismiss 될때 onDismiss 메쏘드가 호출된다.

