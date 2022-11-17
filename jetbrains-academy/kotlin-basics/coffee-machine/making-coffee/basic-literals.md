# Basic literals

## Basic literals

Regardless of their complexity, all programs essentially perform operations on numbers, strings, and other values. These values are called **literals** i.e.

Before we start writing our first programs, let's learn the basic literals in Kotlin: **integer** **numbers**, **characters**, and **strings**. You can meet these literals everywhere in everyday life.

복잡성에 관계없이 모든 프로그램은 기본적으로 숫자, 문자열 및 기타 값에 대한 작업을 수행합니다. 이러한 값을 **리터럴**이라고 합니다.

첫 번째 프로그램을 쓰기 전에, 코틀린의 기본 리터럴인 **정수 숫자**, **문자**, **문자열**에 대해 배워봅시다. 당신은 일상생활 어디에서나 이러한 리터럴들을 만날 수 있다.

### Integer numbers

Here are several examples of valid integer number literals separated by commas: `0`, `1`, `2`, `10`, `11`, `100`.

If an integer value contains a lot of digits, we can add underscores to divide the digits into blocks to make this number more readable: for example, `1_000_000` is much easier to read than `1000000`.

You can add as many underscores as you would like: `1__000_000`, `1_2_3`. Remember, underscores can’t appear at the start or at the end of the number. If you write `_10` or `100_` , you get an error.

### Characters

A single character can represent a digit, a letter, or another symbol. To write a single character, we wrap a symbol in **single quotes** as follows: `'A'`, `'B'`, `'C'`, `'x'`, `'y'`, `'z'`, `'0'`, `'1'`, `'2'`, `'9'`. Character literals can represent alphabet letters, digits from `'0'` to `'9'`, whitespaces (`' '`), or some other symbols (e.g., `'$'`).

Do not confuse characters representing numbers (e.g., `'9'`) and numbers themselves (e.g., `9`).

A character cannot include two or more digits or letters because it represents a single symbol. The following two examples are **incorrect**: `'abc'`, `'543'` because these literals have too many characters.

### Strings

Strings represent text information, such as the text of an advertisement, the address of a web page, or the login to a website. A string is a sequence of any individual characters.

To write strings, we wrap characters in **double quotes** instead of single ones. Here are some valid examples: `"text"`, `"I want to learn Kotlin"`, `"123456"`, `"e-mail@gmail.com"`. So, strings can include letters, digits, whitespaces, and other characters.

A string can also contain just one single character, like `"A"`. Do not confuse it with the character `'A'`, which is not a string.

### Conclusion

Do not confuse these literals:

* `123` is an integer number, and `"123"` is a string;
* `'A'` is a character, and `"A"` is a string;
* `'1'` is a character, and `1` is an integer number.
