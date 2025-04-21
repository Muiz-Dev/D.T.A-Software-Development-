# Vowel Modifier Program

This C# program takes a user-entered sentence and modifies it by adding "ggy" before every vowel (a, e, i, o, u, both lowercase and uppercase). Non-vowel characters remain unchanged. The program then displays both the original and modified sentences. Below is a line-by-line explanation of the code to help understand its functionality.

## Code Explanation

### Namespace and Using Directives

```csharp
using System;
```
Explanation: Imports the System namespace, which provides basic functionalities like Console for input and output operations.

```csharp
using System.Text;
```
Explanation: Imports the System.Text namespace, which includes the StringBuilder class used for efficient string building.

```csharp
namespace VowelModifier
```
Explanation: Defines a namespace called VowelModifier to organize the code and prevent naming conflicts.

```csharp
class Program
```
Explanation: Declares a class named Program that contains all the program's logic.

### Main Method

```csharp
static void Main(string[] args)
```
Explanation: The entry point of the program where execution begins. static means it belongs to the class, and args is for command-line arguments (unused here).

```csharp
Console.WriteLine("Vowel Modifier Program");
Console.WriteLine("=====================");
```
Explanation: Prints a title and a line of equal signs to the console for a clean, formatted output.

```csharp
Console.WriteLine("\nPlease enter a sentence:");
```
Explanation: Prompts the user to enter a sentence. \n adds a blank line for better readability.

```csharp
string? inputSentence = Console.ReadLine();
```
Explanation: Reads the user’s input from the console and stores it in inputSentence. The ? indicates the string can be null if no input is provided.

```csharp
string modifiedSentence = ModifySentence(inputSentence);
```
Explanation: Calls the ModifySentence method with the user’s input and stores the result in modifiedSentence.

```csharp
Console.WriteLine("\nOriginal sentence: " + (inputSentence ?? "No input provided"));
```
Explanation: Prints the original sentence. The ?? operator checks if inputSentence is null; if it is, it displays "No input provided" instead.

```csharp
Console.WriteLine("Modified sentence: " + modifiedSentence);
```
Explanation: Prints the modified sentence returned by the ModifySentence method.

```csharp
Console.WriteLine("\nPress any key to exit...");
```
Explanation: Prompts the user to press a key to close the program.

```csharp
Console.ReadKey();
```
Explanation: Pauses the program, waiting for the user to press any key before exiting.

### ModifySentence Method

```csharp
static string ModifySentence(string? input)
```
Explanation: Defines a method called ModifySentence that takes a string (input) and returns a string. It’s static so it can be called without an object. The input can be null.

```csharp
if (string.IsNullOrEmpty(input))
{
    return string.Empty;
}
```
Explanation: Checks if the input is null or empty. If so, returns an empty string to prevent errors.

```csharp
StringBuilder result = new StringBuilder();
```
Explanation: Creates a StringBuilder object called result to efficiently build the modified string by appending characters.

```csharp
char[] vowels = { 'a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U' };
```
Explanation: Defines an array of vowels (lowercase and uppercase) to check against each character in the input.

```csharp
foreach (char c in input)
```
Explanation: Loops through each character (c) in the input string.

```csharp
if (Array.IndexOf(vowels, c) >= 0)
```
Explanation: Checks if the current character c is a vowel by searching for it in the vowels array. Array.IndexOf returns the index (0 or higher) if found, or -1 if not.

```csharp
result.Append("ggy");
```
Explanation: If the character is a vowel, appends "ggy" to the result (e.g., for 'a', it adds "ggy").

```csharp
else
{
    result.Append(c);
}
```
Explanation: If the character is not a vowel, appends the original character c to the result unchanged.

```csharp
return result.ToString();
```
Explanation: Converts the StringBuilder (result) to a regular string and returns it as the modified sentence.

### Program Functionality

- The program prompts the user to enter a sentence.
- It processes the sentence by inserting "ggy" before every vowel (e.g., "hello" becomes "hggyellggyo").
- Non-vowel characters remain unchanged.
- It displays both the original and modified sentences.

**Example:** Input "cat" → Output "cggyat".

### Why Use StringBuilder?

StringBuilder is used instead of regular string concatenation because strings in C# are immutable (cannot be changed once created). Concatenating strings creates new strings each time, which is inefficient for large inputs. StringBuilder is optimized for building strings incrementally.

