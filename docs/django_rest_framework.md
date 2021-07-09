# Django REST Framework

## Tutorial 1: Serialization

### Introduction

### Getting started

We'll need to add our new `snippets` app and the `rest_framework` app to `INSTALLED_APPS`.

### Creating a model to work with

### Creating a `Serializer` class

The first thing we need to get started on our Web API is to provide a way of serializing and deserializing the snippet instances into representations such as `json`.
We can do this by declaring serializers that work very similar to Django's forms.
Create a file in the `snippets` directory named `serializers.py` and add the following.

### Working with `Serializers`

### Using `ModelSerializers`

In the same way that Django provides both `Form` classes and `ModelForm` classes, REST framework includes both `Serializer` classes, and `ModelSerializer` classes.

Let's look at refactoring our serializer using the ModelSerializer class.
Open the file `snippets/serializers.py` again, and replace the `SnippetSerializer` class with the following.
```python
lass SnippetSerializer(serializers.ModelSerializer):
    class Meta:
        model = Snippet
        fields = ['id', 'title', 'code', 'linenos', 'language', 'style']
```

It's important to remember that `ModelSerializer` classes don't do anything particularly magical, they are simply a shortcut for creating serializer classes:
* An automatically determined set of fields.
* Simple default implementations for the `create()` and `update()` methods.

### Writing regular Django views using our Serializer

Let's see how we can write some API views using our new Serializer class.
For the moment we won't use any of REST framework's other features, we'll just write the views as regular Django views.

## Tutorial 2: Requests and Responses

### Request objects

REST framework introduces a `Request` object that extends the regular `HttpRequest`, and provides more flexible request parsing.
The core functionality of the `Request` object is the `request.data` attribute, which is similar to `request.POST`, but more useful for working with Web APIs.

### Response objects

REST framework also introduces a `Response` object, which is a type of `TemplateResponse` that takes unrendered content and uses content negotiation to determine the correct content type to return to the client.

### Status codes

Using numeric HTTP status codes in your views doesn't always make for obvious reading, and it's easy to not notice if you get an error code wrong.
REST framework provides more explicit identifiers for each status code, such as `HTTP_400_BAD_REQUEST` in the `status` module.
It's a good idea to use these throughout rather than using numeric identifiers.

### Wrapping API views

REST framework provides two wrappers you can use to write API views.
* The `@api_view` decorator for working with function based views.
* The `APIView` class for working with class-based views.

These wrappers provide a few bits of functionality such as making sure you receive `Request` instances in your view, and adding context to `Response` objects so that content negotiation can be performed.

The wrappers also provide behaviour such as returning `405 Method Not Allowed` responses when appropriate, and handling any `ParseError` exceptions that occur when accessing `request.data` with malformed input.

### Pulling it all together

This should all feel very familiar - it is not a lot different from working with regular Django views.

Notice that we're no longer explicitly tying our requests or responses to a given content type.
`request.data` can handle incoming json requests, but it can also handle other formats.
Similarly we're returning response objects with data, but allowing REST framework to render the response into the correct content type for us.

### Adding optional format suffixes to our URLs

To take advantage of the fact that our responses are no longer hardwired to a single content type let's add support for format suffixes to our API endpoints.
Using format suffixes gives us URLs that explicitly refer to a given format, and means our API will be able to handle URLs such as http://example.com/api/items/4.json.

Start by adding a `format` keyword argument to both of the views, like so.

### How's it looking?

## Tutorial 3: Class-based Views

We can also write our API views using class-based views, rather than function based views.
As we'll see this is a powerful pattern that allows us to reuse common functionality, and helps us keep our code DRY.

### Rewriting our API using class-based views

## Tutorial 6: ViewSets & Routers

`ViewSet` classes are almost the same thing as View classes, except that they provide operations such as retrieve, or update, and not method handlers such as get or put.

A `ViewSet` class is only bound to a set of method handlers at the last moment, when it is instantiated into a set of views, typically by using a `Router` class which handles the complexities of defining the URL conf for you.


