# Note Reactions API

- [List note reactions](index.html#list-note-reactions)
- [Create a note reaction](index.html#create-a-note-reaction)
- [Remove a note reaction](index.html#remove-a-note-reaction)
- [Fields](index.html#fields)

## List note reactions

List all note reactions for a note:

```
GET /notes/:id/note_reactions
```

### Response

```
status: 200 OK
```

```
[{"id":5,"reaction":"👍","person":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}}}]
```

The response contains [these fields](index.html#fields) by default. [Pagination](../../general/pagination.html) is available to reduce/limit the collection of note reactions.

## Create a note reaction

```
POST /note_reactions
```

When creating a new note reaction you have to provide a *note\_id* and *reaction* see [the fields section](index.html#fields).

### Response

```
status: 201 Created
```

```
{"id":5,"reaction":"👍","person":{"id":6,"name":"Howard Tanner","account":{"id":"widget","name":"Widget International"}}}
```

## Remove a note reaction

Remove a note reaction with a specific ID.

```
DELETE /note_reactions/:id
```

### Response

```
status: 204 No Content
```

## Fields

id
: *Readonly* **[integer](../../general/data_types.html)** — The unique ID of the note reaction.

note\_id
: *Required* **[reference](../../general/data_types.html#references) to [Note](../../notes.html)**

person
: *Readonly* **[reference](../../general/data_types.html#references) to [Person](../../people.html)**

reaction
: *Required* **[string](../../general/data_types.html)** — The type of reaction to add to the note. Valid values are: 👍 👎 😀 😕 🎉 ❤️.
