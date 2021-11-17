---
title: Comments
---

# Comments

I bet you’re getting bored by now, huh? A lot of this stuff is the same as previous chapters. First, we’ll create a model, then a serializer, followed by a renderer, and eventually a set of views.

## Creating the Comment model

Open `conduit/apps/articles/models.py` and add the following model to the end of the file:
```python
class Comment(TimestampedModel):
    body = models.TextField()

    article = models.ForeignKey(
        'articles.Article', related_name='comments', on_delete=models.CASCADE
    )

    author = models.ForeignKey(
        'profiles.Profile', related_name='comments', on_delete=models.CASCADE
    )
```

The `Comment` model is very simple. Aside from having an `author` and being related to a specific `article`, all this data model has is a text field called `body` for storing the content of the comment.

The next step would be to create and run your migrations as usual.

To generate new migrations, run this command:

```
~ python manage.py makemigrations
```

To apply those new migrations, run this command:

```
~ python manage.py migrate
```
