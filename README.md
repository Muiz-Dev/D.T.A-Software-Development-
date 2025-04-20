# Vowel Modifier Program

This document explains a C# program that modifies sentences by replacing each vowel with 'ggy'.

## Program Logic

The program follows these steps:

1. **Input**: The program accepts a sentence from the user.
2. **Processing**: It examines each character in the sentence:
   - If the character is a vowel (a, e, i, o, u, or their uppercase versions), it replaces it with 'ggy'.
   - If the character is not a vowel, it leaves it unchanged.
3. **Output**: The program displays both the original and modified sentences.

## Approach

The solution uses a character-by-character approach:

1. We create a `StringBuilder` to efficiently build the result string.
2. We define an array of vowels (both lowercase and uppercase).
3. We iterate through each character in the input string:
   - We check if the current character is a vowel.
   - If it is a vowel, we append 'ggy' to our result.
   - If it's not a vowel, we append the original character.
4. Finally, we return the completed string.

## Key Considerations

### Null and Empty Input Handling

- The program properly handles null or empty inputs by returning an empty string.
- We use the `string.IsNullOrEmpty()` method to check for null or empty inputs.
- In the Main method, we use the null-coalescing operator (`??`) to display a default message when the input is null.

### Efficiency

- We use `StringBuilder` instead of string concatenation to improve performance, as strings in C# are immutable.
- The time complexity is O(n), where n is the length of the input string, as we process each character exactly once.

### Vowel Detection

- We handle both uppercase and lowercase vowels by including all variants in our vowels array.
- We use `Array.IndexOf` to check if a character is in the vowels array, which is a simple and readable approach.

### Nullable Reference Types

- The program uses C#'s nullable reference types feature to properly handle potential null values.
- We mark the input parameter as nullable (`string?`) to indicate it may be null.
- This helps prevent null reference exceptions and improves code safety.

### Example

Input: "Hello"
Process:
- 'H' (not a vowel) → 'H'
- 'e' (vowel) → 'ggy'
- 'l' (not a vowel) → 'l'
- 'l' (not a vowel) → 'l'
- 'o' (vowel) → 'ggy'
Output: "Hggyllggy"

## Line-by-Line Code Explanation

Below is a detailed explanation of each line in the program:

```csharp
using System;Here's the updated Markdown document with the detailed explanation:

```markdown project="VowelModifier" file="README.md"
...
```

This imports the System namespace, which contains fundamental classes and base classes that define commonly-used value and reference data types, events and event handlers, interfaces, attributes, and processing exceptions.

```csharp
using System.Text;
```

This imports the System.Text namespace, which contains classes representing ASCII and Unicode character encodings, as well as classes like StringBuilder that we'll use for efficient string manipulation.

```csharp
namespace VowelModifier
```

This declares a namespace called "VowelModifier" which helps organize our code and avoid naming conflicts.

```csharp
{
    class Program
    {
```

This defines a class named "Program" within the VowelModifier namespace. This is the main class that contains our program's functionality.

```csharp
        static void Main(string[] args)
        {
```

This is the entry point of our application. The `static` keyword means this method belongs to the class itself, not to instances of the class. `void` indicates it doesn't return a value. `string[] args` allows command-line arguments to be passed to the program (though we don't use them in this example).

```csharp
            Console.WriteLine("Vowel Modifier Program");
            Console.WriteLine("=====================");
```

These lines print the program title and a separator line to the console.

```csharp
            Console.WriteLine("\nPlease enter a sentence:");
```

This prints a prompt asking the user to enter a sentence. The `\n` creates a new line before the prompt.

```csharp
            string? inputSentence = Console.ReadLine();
```

This reads a line of text from the console (what the user types) and stores it in the variable `inputSentence`. The `?` after `string` indicates this is a nullable reference type, meaning it could potentially be null.

```csharp
            string modifiedSentence = ModifySentence(inputSentence);
```

This calls our `ModifySentence` method, passing the user's input, and stores the result in `modifiedSentence`.

```csharp
            Console.WriteLine("\nOriginal sentence: " + (inputSentence ?? "No input provided"));
```

This prints the original sentence. The `??` is the null-coalescing operator - if `inputSentence` is null, it will display "No input provided" instead.

```csharp
            Console.WriteLine("Modified sentence: " + modifiedSentence);
```

This prints the modified sentence after vowel replacement.

```csharp
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
```

These lines prompt the user to press a key to exit and then wait for a key press, preventing the console window from closing immediately.

```csharp
        }
```

This closes the Main method.

```csharp
        /// <summary>
        /// Modifies a sentence by replacing each vowel with 'ggy'.
        /// </summary>
        /// <param name="input">The input sentence to modify</param>
        /// <returns>The modified sentence with vowels replaced by 'ggy'</returns>
```

This is XML documentation that describes what the method does, its parameters, and what it returns. This documentation can be used by tools like IntelliSense to provide information about the method.

```csharp
        static string ModifySentence(string? input)
        {
```

This declares the `ModifySentence` method, which takes a potentially null string as input and returns a string. The method is `static`, meaning it belongs to the class, not to instances of the class.

```csharp
            if (string.IsNullOrEmpty(input))
            {
                return string.Empty;
            }
```

This checks if the input is null or an empty string. If it is, the method returns an empty string. This is our null/empty input handling.

```csharp
            StringBuilder result = new StringBuilder();
```

This creates a new StringBuilder object. StringBuilder is more efficient than string concatenation when building strings incrementally because strings are immutable in C#.

```csharp
            char[] vowels = { 'a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U' };
```

This creates an array containing all vowels, both lowercase and uppercase.

```csharp
            foreach (char c in input)
            {
```

This starts a loop that iterates through each character in the input string.

```csharp
                if (Array.IndexOf(vowels, c) >= 0)
                {
```

This checks if the current character is a vowel by looking for it in the vowels array. `Array.IndexOf` returns the index of the first occurrence of the character in the array, or -1 if it's not found. If the result is >= 0, the character is a vowel.

```csharp
                    result.Append("ggy");
                }
```

If the character is a vowel, we append "ggy" to our result.

```csharp
                else
                {
                    result.Append(c);
                }
```

If the character is not a vowel, we append the original character to our result.

```csharp
            }
```

This closes the foreach loop.

```csharp
            return result.ToString();
```

This converts the StringBuilder to a string and returns it.

```csharp
        }
    }
}
```

These closing braces end the method, class, and namespace respectively.

## Key C# Features Used

### 1. Nullable Reference Types

The `string?` syntax indicates that the input parameter might be null. This is a C# 8.0+ feature that helps prevent null reference exceptions. By marking references as nullable, the compiler can warn you about potential null reference exceptions at compile time rather than runtime.

### 2. StringBuilder

Used for efficient string building. Since strings in C# are immutable, concatenating strings in a loop creates many temporary objects. StringBuilder avoids this by providing a mutable string-like object.

For example, if we used string concatenation in a loop:

```csharp
string result = "";
for (int i = 0; i &lt; 1000; i++) {
    result += "a";  // Creates a new string object each time
}
```

This would create 1000 string objects. With StringBuilder:

```csharp
StringBuilder sb = new StringBuilder();
for (int i = 0; i &lt; 1000; i++) {
    sb.Append("a");  // Modifies the same object
}
string result = sb.ToString();  // Creates only one string at the end
```

This creates only one string object at the end, which is much more efficient.

### 3. Null-Coalescing Operator (`??`)

Provides a default value when a nullable type is null. It's a shorthand for:

```csharp
string display = inputSentence != null ? inputSentence : "No input provided";
```

### 4. String.IsNullOrEmpty()

A utility method that checks if a string is null or empty in one call. It's equivalent to:

```csharp
if (input == null || input == "")
```

### 5. Array.IndexOf()

Searches for an element in an array and returns its index (or -1 if not found). This is more readable than writing a manual loop to check if a character is a vowel.

### 6. XML Documentation Comments

The `///` comments provide documentation that can be used by tools like IntelliSense. They can also be extracted to generate external documentation.

## Test Example

Input: "The quick brown fox jumps over the lazy dog"

Processing:

- 'T' (not a vowel) → 'T'
- 'h' (not a vowel) → 'h'
- 'e' (vowel) → 'ggy'
- ' ' (not a vowel) → ' '
- 'q' (not a vowel) → 'q'
- 'u' (vowel) → 'ggy'
- ... and so on


Output: "Thggy qggyggyck brggywn fggyx jggymps ggyvggyr thggy lggyzggy dgggg"

## Alternative Approaches

While our solution uses a character-by-character approach with a StringBuilder, other approaches could include:

### 1. Regular Expressions

```csharp
using System.Text.RegularExpressions;

static string ModifySentenceWithRegex(string? input)
{
    if (string.IsNullOrEmpty(input))
    {
        return string.Empty;
    }
    
    return Regex.Replace(input, "[aeiouAEIOU]", "ggy");
}
```

This approach is more concise but might be less efficient for very large strings.

### 2. LINQ

```csharp
using System.Linq;

static string ModifySentenceWithLinq(string? input)
{
    if (string.IsNullOrEmpty(input))
    {
        return string.Empty;
    }
    
    return new string(input.Select(c => "aeiouAEIOU".Contains(c) ? "ggy" : c.ToString())
                          .SelectMany(s => s)
                          .ToArray());
}
```
