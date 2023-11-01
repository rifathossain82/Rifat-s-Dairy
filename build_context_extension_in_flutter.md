# Let's talk about the BuildContext extension in Flutter

<p>Extensions allow you to organize your code by grouping related functionality together. This helps in maintaining a clean and structured codebase.</p>  
Today we will explore about that.


![with_extention](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/8aae5b26-e33b-45e1-ae01-d64d309f5bc8)
![without_extention](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/83ea9987-44ac-4d1e-b601-6e94429f31be)
![build_context_extension](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/8c72242a-1812-4dd0-ae37-2e9252da0922)

## Step 1:  

##### Add dependencies in pubspec.yaml file:

```yaml
dependencies:
  flutter_dotenv: ^5.0.2
```
  

## Step 2:  

##### Create a **.env** file in your root project folder

![image](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/c9f13b58-e2f5-4e2d-b016-b0091f383c52)  


## Step 3:

##### Add the File Paths in pubspec.yaml file


```yaml
  assets:
    - .env
```



## Step 4: 

##### Initialize the dotenv file in main fuction


```dart
Future<void> main() async {

  /// To initialize dotenv
  await dotenv.load(fileName: ".env");

  runApp(const MyApp());
}
```


####  
##### Welcome! We are done. Now we need to add variables in .env file and use them.


## To add variable in .evn file

```env
# This is a comment
VARIABLE_NAME = VALUE
```


### Example:

```env

# API Base URL
BASE_URL = your_api_base_url

# API Keys
PUBLIC_KEY = your_api_public_key
PRIVATE_KEY = your_api_private_key
```


## To get .env values in your projects just call like that

```dart
  dotenv.env['your_env_variable_name']
```

## Example:

```dart
class Config{
  static String? get baseURL => dotenv.env['BASE_URL'];
  static String? get publicKey => dotenv.env['PUBLIC_KEY'];
  static String? get privateKey => dotenv.env['PRIVATE_KEY'];
}
```

