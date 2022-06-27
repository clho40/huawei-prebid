# Huawei - Prebid Mobile SDK (Android) Implementation
In order to serve Huawei Ads via Prebid Mobile SDK, you must:
1. Include OAID in the ad request

## How to add OAID to the TargetingParams
### 1. build.gradle (Project-level)
```
buildscript {
    repositories {
        ...
        maven { url 'https://developer.huawei.com/repo/' } //Add this repository
    }
    ...
}
```

### 2. build.gradle (Module-level)
```
dependencies {
    implementation 'com.huawei.hms:ads-identifier:<latest_version>' //Add this repository
}
```
Latest version can be found [here](https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides/identifier-service-version-change-history-0000001050066927)

### 3. Get and add OAID to TargetingParams UserData
```
import com.huawei.hms.ads.identifier.AdvertisingIdClient
...
    override fun onCreate(savedInstanceState: Bundle?) {
        ...
        Thread {
            val info = AdvertisingIdClient.getAdvertisingIdInfo(applicationContext)
            TargetingParams.addUserData("oaid", info.id)
        }.start()
    }
```

Detailed implementation guide [here](https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides/identifier-service-integrating-sdk-0000001056460552)

