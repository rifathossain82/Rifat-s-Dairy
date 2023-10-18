### How to Add .env File in Flutter?

<p>In Flutter (and in software development in general), it's a best practice to separate configuration settings and sensitive information from your source code. The reason for this is primarily for security, maintainability, and flexibility.</p>  
Today we will learn, how we can do it?

<br><br>
## Step 1:  

##### Add dependencies in pubspec.yaml file:

```yaml
dependencies:
  flutter_dotenv: ^5.0.2
```
  
<br><br>
## Step 2:  

##### Create a **.env** file in your root project folder

![image](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/263e578a-fbed-4683-9e54-88d5e65faa91)


<br><br>
## Step 3:

##### Add the File Paths in pubspec.yaml file


```yaml
  assets:
    - .env
```


<br><br>
## Step 4: 

##### Initialize the dotenv file in main function


```dart
Future<void> main() async {

  /// To initialize dotenv
  await dotenv.load(fileName: ".env");

  runApp(const MyApp());
}
```


<br><br>
##### Welcome! We are done. Now we need to add variables in .env file and use them.


## Step 5:

##### To add variable in .evn file

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

<br><br>
## Step 6:

##### To get .env values in your projects just call like that

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

<br><br>
## Step 7:

##### Don't forget to add .env in your gitignore file

![image](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/9608321c-062a-4ef7-902e-cc5db1cde311)
