### Hi Folks!

A few days ago I talked about Flutter Dotenv for separating sensitive data [dotenv_in_flutter](https://www.linkedin.com/posts/rifathossain82_in-flutter-and-in-software-development-in-activity-7120378965944369152-SmXU?utm_source=share&utm_medium=member_desktop)

Thanks [Amirul Islam](https://www.linkedin.com/in/amirulcs/) bro for letting me know that dotenv can't hide variables properly.
Since we need to add the file path to pubspec.yaml as an assets, cracking the env variable is easy [Checkout This](https://systemweakness.com/why-not-to-use-dotenv-on-flutter-5d3a07abc971)

Another way I found to overcome this problem is env with obfuscation which adds an extra layer of protection. I recommend that, if you have an API key that you cannot afford to lose, you should store it on the server.

#### Let's go to the alternative way of dotenv

## Step 1:  

##### Add this packages in pubspec.yaml:

```yaml
dependencies:
  envied: ^0.3.0+3

dev_dependencies:
  flutter_test:
    sdk: flutter
  flutter_lints: ^2.0.0
  envied_generator: ^0.3.0+3
  build_runner: any
```

<br><br>
## Step 2:  

Create a **.env** file in your root project folder

![Screenshot 2023-11-05 234359](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/07f55422-6d75-401f-865f-5ddcf4932d3f)

<br>

Then add variables like this

```.env
AGORA_APP_ID = bde38aef8d94644a000000000000000
AGORA_TOKEN = 98b6407f28149ff92000000000000000
```


<br><br>
## Step 3:  

Create an env folder in lib folder then add this ***env.dart**

```dart
import 'package:envied/envied.dart';

part 'env.g.dart';

/// Here the env data comes from the root project's .env file
/// So, I need to declare the path as '.env'
/// Don't forget to generate 'env.g.dart' file

@Envied(path: '.env')
abstract class Env {
  @EnviedField(varName: 'AGORA_APP_ID', obfuscate: true)
  static final agoraAppId = _Env.agoraAppId;

  @EnviedField(varName: 'AGORA_TOKEN', obfuscate: true)
  static final agoraToken = _Env.agoraToken;
}

```

<br><br>

# Step 4: 

Run this command in your terminal to generate ***env.g.dart*** file
```command
flutter pub run build_runner build --delete-conflicting-outputs
```

Then it will create a file like this

``` dart
// GENERATED CODE - DO NOT MODIFY BY HAND

part of 'env.dart';

// **************************************************************************
// EnviedGenerator
// **************************************************************************

class _Env {
  static const List<int> _enviedkeyagoraAppId = [
    188181602,
    2492606913,
    3945196090,
    509818639,
    2114499327,
    789953343,
    1253127060,
    1189679537,
    916108570,
    3886129851,
    1385312852,
    945971108,
    2984679524,
    152267345,
    2776200940,
    1216802548,
    1463226669,
    3190578446,
    2525629242,
    2668258842,
    3134961724,
    863374411,
    1225607862,
    4095272972,
    2049016021,
    2350137293,
    3235470149,
    3443680734,
    3496068194,
    225868909,
    1440260341
  ];
  static const List<int> _envieddataagoraAppId = [
    188181504,
    2492606885,
    3945196127,
    509818684,
    2114499271,
    789953374,
    1253127153,
    1189679575,
    916108578,
    3886129887,
    1385312877,
    945971088,
    2984679506,
    152267365,
    2776200920,
    1216802453,
    1463226653,
    3190578494,
    2525629194,
    2668258858,
    3134961676,
    863374459,
    1225607814,
    4095273020,
    2049016037,
    2350137341,
    3235470197,
    3443680750,
    3496068178,
    225868893,
    1440260293
  ];
  static final agoraAppId = String.fromCharCodes(
    List.generate(_envieddataagoraAppId.length, (i) => i, growable: false)
        .map((i) => _envieddataagoraAppId[i] ^ _enviedkeyagoraAppId[i])
        .toList(growable: false),
  );
  static const List<int> _enviedkeyagoraToken = [
    2487759220,
    416570242,
    942000533,
    696769051,
    2928492257,
    1545536659,
    3700725112,
    1504425370,
    2828547707,
    3425057617,
    132350537,
    2774150667,
    55487504,
    4221643426,
    2141256846,
    3607848124,
    3044430024,
    4254948397,
    3657087798,
    2669808850,
    493743360,
    2173861511,
    2830441711,
    677632232,
    3763498738,
    654098859,
    956379864,
    68426688,
    432979218,
    1640039816,
    405477422,
    919622206
  ];
  static const List<int> _envieddataagoraToken = [
    2487759181,
    416570298,
    942000631,
    696769069,
    2928492245,
    1545536675,
    3700725071,
    1504425468,
    2828547657,
    3425057641,
    132350584,
    2774150719,
    55487529,
    4221643460,
    2141256936,
    3607848069,
    3044430074,
    4254948381,
    3657087750,
    2669808866,
    493743408,
    2173861559,
    2830441695,
    677632216,
    3763498690,
    654098843,
    956379880,
    68426736,
    432979234,
    1640039864,
    405477406,
    919622158
  ];
  static final agoraToken = String.fromCharCodes(
    List.generate(_envieddataagoraToken.length, (i) => i, growable: false)
        .map((i) => _envieddataagoraToken[i] ^ _enviedkeyagoraToken[i])
        .toList(growable: false),
  );
}

```


<br><br>

# Step 5:

Create a .gitignore file in the env folder then add this line

```gitignore
env.g.dart
```


Also add this line in the root .gitignore file

```gitignore
*.env
```

<br><br>

# Step 6: 

To use variables:

```dart
print('App Id: ${Env.agoraAppId}');
print('Token: ${Env.agoraAppId}');
```

<br>

Finally our env folder will look like this 

![Screenshot 2023-11-06 001630](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/136c5e8d-dac9-4234-9fb3-097a67995f45)



<br><br>
[Checkout this to learn more](https://codewithandrea.com/articles/flutter-api-keys-dart-define-env-files/)


