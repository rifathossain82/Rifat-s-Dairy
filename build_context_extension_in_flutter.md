# Let's talk about the BuildContext extension in Flutter

<p>Extensions allow you to organize your code by grouping related functionality together. This helps in maintaining a clean and structured codebase.</p>  
Today we'll learn how we can simplify your code using the build context extension.

<br>
<br>

### First check this widget:

![without_extention](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/83ea9987-44ac-4d1e-b601-6e94429f31be)

<br>
<br>

> 1. When obtaining the screen size, developers often resort to **MediaQuery.of(context).size** repeatedly. You might wonder, why not create a method? The answer lies in the power of extensions, waiting for you to simplify your code effortlessly.

> 2. When accessing the primary color from the app theme, developers frequently rely on **Theme.of(context).primaryColor**. But did you know, you can streamline this to **context.primaryColor** using the BuildContext extension? We can also bring other colors this way.

> 3. I've observed numerous developers on GitHub relying heavily on the TextStyle method to implement text styles. However, accessing the default app text theme is as straightforward as using the context directly. This is where the BuildContext extension proves invaluable, significantly reducing the complexity of this code segment.

<br>

look at that: here I use poppins TextTheme as a default text theme for light theme.

```dart
  static final ThemeData lightTheme = ThemeData(
    brightness: Brightness.light,
    textTheme: GoogleFonts.poppinsTextTheme(Typography.blackCupertino),
  );
```

To implement light text theme for dark theme, just I change text theme property, that's it.

```dart
  static final ThemeData darkTheme = ThemeData(
    brightness: Brightness.dark,
    textTheme: GoogleFonts.poppinsTextTheme(Typography.whiteCupertino),
  );
```


<br>
<br>

# Example of build context extension:
![build_context_extension](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/8c72242a-1812-4dd0-ae37-2e9252da0922)


<br>
<br>

# Using the buildContext extension on the widget:
![with_extention](https://github.com/rifathossain82/Rifat-s-Dairy/assets/88751768/8aae5b26-e33b-45e1-ae01-d64d309f5bc8)

