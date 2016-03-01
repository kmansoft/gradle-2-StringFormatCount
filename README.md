# gradle-2-StringFormatCount
Test app for issue with Lint StringFormatCount in gradle tools 2.0

### When building with tools 2.0:

> /home/kman/Documents/gradle-2-StringFormatCount/res/values-fr/strings.xml:3: Error: Inconsistent number of arguments in formatting string test_string; found both 0 and 1 [StringFormatCount]
>  <string name="test_string">Pretend this is French - %1$d</string>
>  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     /home/kman/Documents/gradle-2-StringFormatCount/res/values/strings.xml:7: Conflicting number of arguments here
> 
>    Explanation for issues of type "StringFormatCount":
>    When a formatted string takes arguments, it usually needs to reference the
>    same arguments in all translations (or all arguments if there are no
>    translations.
> 
>    There are cases where this is not the case, so this issue is a warning
>    rather than an error by default. However, this usually happens when a
>    language is not translated or updated correctly.
> 
> 1 errors, 0 warnings
> :lintVitalRelease FAILED

### When building with tools 1.5:

No errors

The way I have test_string and test_string_en may seem weird, but the idea is to: 1) provide an always accessing English string (if the user chooses a setting to "always send this text in English") and 2) to use it as a fallback for other languages.

Usually there will be translations for test_string (and the _en value will remain accessible from code, no matter what the language), but not always (and then test_string will pick up the _en's value).
