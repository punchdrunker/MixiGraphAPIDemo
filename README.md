MixiGraphAPIDemo
================

for PHDJ

# mixi Graph API

http://developer.mixi.co.jp/connect/mixi_graph_api/mixi_io_spec_top/

# Getting Started with mixi Graph API 

## mixiアカウントの登録

http://mixi.jp

(携帯電話番号の登録が必要です)

## パートナー登録

http://developer.mixi.co.jp/about-platform/com/developer/

(クレジットカードの登録が必要です)

## アプリ作成

https://sap.mixi.jp/home.pl

## SDKを使う

### SDK Document for iOS

http://developer.mixi.co.jp/connect/mixi_graph_api/ios/

### SDK Document for Android

http://developer.mixi.co.jp/connect/mixi_graph_api/android/

#### SDK初期化 ####

application:didFinishLaunchingWithOptions:内でオブジェクト初期化を行う

    Mixi *mixi = [[Mixi sharedMixi] setupWithType:kMixiApiTypeSelectorMixiApp
                                         clientId:@"mixiapp-web_?????"
                                           secret:@"your-secret-string"
                                      redirectUrl:@"your-redirect-url"];

    [mixi restore];

#### 認証/認可 ####

viewDidAppear以降に以下のような記述で認証/認可画面を表示

    Mixi *mixi = [Mixi sharedMixi];
    if (![mixi isAuthorized]) {
        mixi.authorizer.parentViewController = [self parentViewController];
        mixi.authorizer.delegate = self;
        [mixi authorize:@"r_profile", @"r_voice", nil];
    }

#### APIリクエスト ####

    Mixi *mixi = [Mixi sharedMixi];
    if ([mixi isAuthorized]) {
        MixiRequest *request = [MixiRequest requestWithEndpoint:@"/people/@me/@friends"];
        [mixi sendRequest:request delegate:self];
    }

# Documents

### Sample for iOS App
https://github.com/punchdrunker/MixiApiSDKSample-iOS

### Sample for Android App
https://github.com/mixi-inc/mixi-api-sdk-android-sample

### 第2回　mixi SDKでAndroidアプリを作ろう(gihyo.jp)
http://gihyo.jp/dev/serial/01/mixi_socialapp/0002?page=1
