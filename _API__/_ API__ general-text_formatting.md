# Text Formatting

It is possible to apply basic formatting to text in fields in which multiple lines of text can be entered.

The sections below describe these options.

## Inline styles

bold
: Place text between two asterisks.

 `**Bold**`

italic
: Place text between two underscores.

 `__Italic__`

underline
: Place text between plus signs.

 `+Underline+`

monospace
: Place text between back quotes.

 `` `Monospace` ``

strikethrough
: Place text between tilde signs.

 `~Strikethrough~`

text color
: Place text between `<c #ff0000>` and `</c>` to set the background color, replacing `ff0000` with the desired [hexadecimal color](https://www.w3schools.com/colors/colors_hexadecimal.asp).

 `<c #0000ff>Blue text</c>`

background color
: Place text between `<m #ff0000>` and `</m>` to set the background color, replacing `ff0000` with the desired [hexadecimal color](https://www.w3schools.com/colors/colors_hexadecimal.asp).

 `<m #00ff00>Text with a green background</m>`

## Blocks

The options below can be used to create *blocks* such as lists, quotes and code blocks.
Make sure you separate a block from other content by adding a blank line above and below the block.

numbered list
: Start each line with `1.` to make a numbered list. It does not matter which number you specify; the numbers are corrected automatically when the list is displayed. Nested lists can be created by indenting three spaces so that the nested items line up with the start of the text of the higher-level items.

```
 Follow these steps:

 1. Log in
 2. Open a new record
 3. Enter the following values:
 1. Value A
 2. Value B
 4. Press the Save button

 Result: the record is saved.
```

bulleted list
: Start each line with an asterisk to make a bulleted list. Nested lists can be created by indenting two spaces, so that the nested items line up with the start of the text of the higher-level items.

```
 Follow these steps:

 * Log in
 * Open a new record
 * Enter the following values:
 * Value A
 * Value B
 * Press the Save button

 Result: the record is saved.
```

quote
: Start each line with an angle bracket to make a quote.

```
 As someone once said:

 > Some say that dogs are as smart as people,
 > but some may find that offensive.

 We will probably never know if that's true.
```

code block
: Start and end a code block with three back quotes on an otherwise empty line. Be sure to include a blank line above and below the code block.

```
 To convert an email address to lowercase:

 ```
 var $email = $extension.find('#email_address');
 $email.on('change', function() {
 $email.val($email.val().toLowerCase());
 });
 ```

 This paragraph comes after the code block.
```

## Other

header
: Start a line of text with between one and six `#` signs to insert a header. Make sure to add a blank line above and below.

```
 This paragraph comes before the header.

 ## This is a level 2 header

 This paragraph comes after the header.
```

horizontal rule
: Place three hyphens on an otherwise empty line with a blank line above and below.

```
 This results in a horizontal rule:

 ---

 This paragraph comes after the horizontal rule.
```

hyperlink
: Use the pattern `[text](url)` to create a link.

```
 [Xurrent](https://xurrent.com)
```

image
: Use the pattern `![alt text](image url)` to insert an image.

```
 ![Xurrent logo](https://xurrent.com/images/Xurrent_Logo_122x50.png)
```

mention
: Use the pattern `<@id|display name>` to mention a person from a note. The mention will be shown as a hyperlink with
 text ‘@'.

```
 <@209|Ellen Brown>: Could you please take a look?
```

record reference
: Use the pattern `<record type#id>` to reference a record. The reference will be shown as a hyperlink to
 users that are allowed to see the referenced record. Which record types are supported depends on the record the
 text field belongs to. Example record type values for a note on a request are `request`, `problem`, `workflow`,
 `task` and `knowledge_article`.

```
 Please update <knowledge_article#90>.
```

table
: Tables start with `<table>` and end with `</table>`. Make sure to add a blank line above and below.
 A table consists of one or more rows. Each row must be surrounded with `<tr>` and `</tr>`.
 A table row consists of cells, which can either be normal cells or header cells.
 Each normal cell must be surrounded with `<td>` and `</td>`.
 Each header cell must be surrounded with `<th>` and `</th>`.
 The text in each cell must be on a line by itself.

```
 This paragraph comes before the table.

 <table><tr><th>
 Row 1, header cell 1
 </th><th>
 Row 1, header cell 2
 </th></tr><tr><td>
 Row 2, cell 1
 </td><td>
 Row 2, cell 2
 </td></tr></table>

 This paragraph comes after the table.
```
