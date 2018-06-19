# FAQ

## 지문 인식 센서가 없는 경우

키를 KeyStore에 보관하면 키를 꺼내기 위해서는 안드로이드의 인증 API를 통해야만 KeyStore에 접근할 수 있다. 지문인증 모듈이 없는 경우 KeyStore의 접근권한을 패스워드나 패턴으로 획득하고, Key Store에 접근하면 된다.

## Lock Out

일부 기기에서 Lock Out이 발생할 수 있는데, 이는 지극히 정상적인 현상이다. 구글은 안드로이드 제조업체에게 인증 수단\(패스워드, 패턴그리기, 지문인증\)에 관계없이 5회 연속 실패할 경우, 30초간 인증 시도를 하지 못하도록 가이드하고 있으며 이 기간을 Lock Out이라 부른다. Lock Out은 강력한 보안을 유지하기 위한 수단으로 LockOut이 발생할 경우, 이를 사용자에게 고지하고 Lock Out이 끝난후 인증을 시도하도록 가이드해야 한다. 자세한 사항은 아래의 문서를 참고한다.

[https://source.android.com/compatibility/android-cdd.pdf](https://source.android.com/compatibility/android-cdd.pdf)

