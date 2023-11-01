### How to Add .env File in Flutter?

<p>In Flutter (and in software development in general), it's a best practice to separate configuration settings and sensitive information from your source code. The reason for this is primarily for security, maintainability, and flexibility.</p>  
Today we will learn, how we can do it?


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

