# Comments

You can get a list of comments in your document using the `figmaPlus.comments` API.

## Comment object

The Comment object contains information about your comment, such as its ID, message and author.

You can learn more about comment properties from [Figma's API documentation](https://www.figma.com/developers/docs#comments-types).

### threads

Get an array of all comment threads in your document. A thread can be a single comment, or a comment with replies (listed inside the `replies` array).

```javascript
figmaPlus.comments.threads;
```

### findAll

Find all comments that the `callback` function returns true. If `callback` is not provided, this will returns all comments (both local and published).

```javascript
figmaPlus.comments.findAll(callback);
```

- **callback (optional)** (`Function`): Function to test each comment against.

```javascript
// Return all comments:
figmaPlus.comments.findAll();

// Return all effect comments:
figmaPlus.comments.findAll(comment => comment.type === 'EFFECT');
```

### findOne

Find the first comment the `callback` function returns true. If no results are found, it will return `null`.

```javascript
figmaPlus.comments.findOne(callback);
```

- **callback** (`Function`): Function to test each comment against.

```javascript
// Find the first descendent of a node named 'Primary Color'
figmaPluscomments.findOne(comment => comment.name === 'Primary Color');
```

## getCommentById

Get a comment by its ID.

```javascript
figmaPlus.getCommentById(commentId);
```
