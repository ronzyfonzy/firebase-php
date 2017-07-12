# Firebase Admin SDK for PHP

[![Latest Stable Version](https://poser.pugx.org/kreait/firebase-php/v/stable)](https://packagist.org/packages/kreait/firebase-php)

This SDK makes it easy to interact with [Google Firebase](https://firebase.google.com>)
applications.

## Security fixes only

The 2.x branch of this library is supported for critical security issues only.
Releases are only made on an as-needed basis.

Please use the [latest stable version](https://github.com/kreait/firebase-php/releases/latest).

---

## Documentation

You can find the documentation at http://firebase-php.readthedocs.io/en/2.x/

## Usage example

```php
$firebase = (new \Firebase\Factory())
    ->withCredentials(__DIR__.'/path/to/google-service-account.json')
    ->withDatabaseUri('https://my-project.firebaseio.com')
    ->create();

$database = $firebase->getDatabase();

$newPost = $database
    ->getReference('blog/posts')
    ->push([
        'title' => 'Post title',
        'body' => 'This should probably be longer.'
    ]);

$newPost->getKey(); // => -KVr5eu8gcTv7_AHb-3-
$newPost->getUri(); // => https://my-project.firebaseio.com/blog/posts/-KVr5eu8gcTv7_AHb-3-

$newPost->getChild('title')->set('Changed post title');
$newPost->getValue(); // Fetches the data from the realtime database
$newPost->remove();
```
