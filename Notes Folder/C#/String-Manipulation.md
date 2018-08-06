# String Manipulation

<!-- TOC -->

- [String Manipulation](#string-manipulation)
- [Replace Text](#replace-text)
    - [string.Replace](#stringreplace)
- [Trim](#trim)
- [Remove Text](#remove-text)
- [Replace Matching Patterns](#replace-matching-patterns)
- [Modifiying Individual Characters](#modifiying-individual-characters)
- [Unsafe Modification(s) to String(s)](#unsafe-modifications-to-strings)

<!-- /TOC -->

# Replace Text
## string.Replace

* Creates a new string containing the modifications you apply
    - can be used to ***Replace*** either strings or single characters (Chars). In ***Both*** cases, ***Every*** occurrence of the Sought text ***is*** replaced!

    <h3> Source String(s) <b><i>Will</i></b> remain Unchanged! </h3>
    
# Trim


* string.Trim():
    - removes leading AND following whitespace(s).
* string.TrimStart():
    - removes Leading whitespace(s).
* string.TrimEnd():
    - removes Trialing/Ending whitespace(s)

# Remove Text

* string.Remove():
    - used to remove text from a string. This method removes a # of chars. starting at a ***Specific*** index.
        + ***indexOf()*** method can be used to get index of a specific Char. to feed into the method.

# Replace Matching Patterns

* You can use matching expressions to replace text matching a ***pattern*** with new text, *Possibly* defined by a pattern.
    - The *system.text.RegularExpressions.Regex* method is One way to do so.
        + the *Regex.Replace(string, string, MatchEvaluator, RegexOptions)* method takes a function that *provides* the logic of a replacement as on of its Args.

### Regular Expressions are most useful for searching and replacing text that follows a pattern, rather than ***Known Text***.

* Ex:
    - the pattern 'the\s' searches for the word 'The' followed by a whitespace character, that part of the pattern ensures it ***DOES NOT*** match 'There' in the source string.


```C#
    string source = "The mountains are still there behind the clouds today.";

    // Use Regex.Replace for more flexibility. 
    // Replace "the" or "The" with "many" or "Many".
    // using System.Text.RegularExpressions
    string replaceWith = "many ";
    source = System.Text.RegularExpressions.Regex.Replace(source, "the\\s", LocalReplaceMatchCase, 
    System.Text.RegularExpressions.RegexOptions.IgnoreCase);
        Console.WriteLine(source);

    string LocalReplaceMatchCase(System.Text.RegularExpressions.Match matchExpression)
    {
        // Test whether the match is capitalized
        if (Char.IsUpper(matchExpression.Value[0]))
        {
            // Capitalize the replacement string
            System.Text.StringBuilder replacementBuilder = new System.Text.StringBuilder(replaceWith);
            replacementBuilder[0] = Char.ToUpper(replacementBuilder[0]);
            return replacementBuilder.ToString();
        }
        else
        {
            return replaceWith;
        }
    }
```

### The StringBuilder.ToString() method returns a(n) immutable object with the content of the StringBuilder Object in the Example Given. 

# Modifying Individual Characters

* You can produce a character array from a string, modify the content of said array, and *then* create a new string from the modified contents of the array.

    -Uses the *ToCharArray()* method to create a(n) array of the strings characters then uses the *indexOf* method to find the points we want to replace.

# Unsafe Modification(s) to String(s)

* Using 'unsafe' code you can modify a string '*in place*' *after* it has been created. <u> Unsafe code bypasses many of the features .NET designed to minimize certain type of bugs in code. </u>

### It is *Highly* recommended against unless ***Absolutely*** necessary. ###