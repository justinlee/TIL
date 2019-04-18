오늘 공부한 내용.

다음 코드를 보자.

[UNUserNotificationCenter currentNotificationCenter].delegate = self;
UNAuthorizationOptions authOptions = UNAuthorizationOptionAlert | UNAuthorizationOptionSound | UNAuthorizationOptionBadge;
        
//----------------------------------------------------------------
// 이부분이 중요함.
if (@available(iOS 12.0, *)) {
  authOptions = authOptions | UNAuthorizationOptionProvisional;
}
//----------------------------------------------------------------
        
[[UNUserNotificationCenter currentNotificationCenter] requestAuthorizationWithOptions:authOptions
                                                                    completionHandler:^(BOOL granted, NSError * _Nullable error) {
                                                                    }];

UNAuthorizationOptionProvisional 의 경우엔 iOS 12에서 추가된 기능으로 앱이 처음 실행될때 푸시 동의 얼럿을 띄우지 않고 임시 푸시를 보낼수 있음.
단, 푸시 리스트쪽에서만 확인이 가능하고, 제대로 푸시를 받으려면 푸시를 선택해서 동의를 해야만 제대로 푸시를 받을수 있음.

