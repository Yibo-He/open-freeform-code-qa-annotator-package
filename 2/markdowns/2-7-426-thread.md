
# Post \#62967224 [Link](https://stackoverflow.com/questions/62967224/)

## How to solve "CSRF Token Mismatch" in Laravel

**Vote**: 8 (428/702) **Views**: 17489 (326/702) 

**Internal ID** \#2-7-426

Created at 2020-07-18 10:03:06

Tags: `php` `laravel` `csrf`

----------

#### Metadata:

Area: `Back-end`

Language: `php` (full parsed tag list: `php`)

----------

**Notepad**


----------

I am working on a laravel application. Upon hosting it on my domain, I am running into a "CSRF token mismatch" error. Locally, the application is working fine because I have included the csrf token in the header as shown in the documentation. Therefore, the csrf token is being generated successfully and being included in the header of requests. On doing some debugging, I changed the `SESSION_DRIVER` in env file to `file` so that I can see the sessions. I realized that multiple sessions are being generated for one user. The `SESSION_LIFETIME` is set to `120`, which I believe is okay. In looking at the tokens in the sessions stored in `storage/framework/sessions`, none contains the token that is generated by the browser. What could be the issue? Remember that it is working fine locally. What configurations on the host domain could be affecting the sessions of the application.


----------
        
## Answer \#0

**Accepted** Vote: 15

Created at 2020-07-18 10:48:28

------------

I once ran into the same error while hosting in the cPanel and took me almost 3days to figure out the solution for my case.
I do not know if this works for you but give it a try.
Inside your main index.php file inside the public folder, edit it and at the very top after starting PHP tags, write
```
ob_start()
```

This function will take the contents of the output buffer and returns a string that is to be sent to the browser for rendering and removes the spaces or line breaks you put before starting PHP.
Also, try clearing the cache as suggested in the comments.
Let me know if this helps you as well.


------------
    
    
## Answer \#1

 Vote: 3

Created at 2021-03-28 11:30:52

------------

Add the following line to the head tag.
```
<meta name="csrf-token" content="{{ csrf_token() }}"> // Add in <head></head>
```

Then get you can get this content attribute in Laravel. Also, in your script tag, add the following code (this is to make sure when you submit the form, you get the correct `csrf_token`).
```
$.ajaxSetup({
    headers: {
        'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
    }
});
```



------------
    
    
## Answer \#2

 Vote: 3

Created at 2021-08-06 14:23:40

------------

I had this very same problem, receiving the "CSRF Token Mismatch" exception in Laravel 7, having fixed everything else, like setting the csrf token on page header, in ajax requests, clearing the cache, anything you can think of and usually find in solution proposals.
So, if anyone ever runs into this, I haven't found this solution anywhere else, and it really cost me hours.
I had called the application on the wrong URL!
I used my local IP literally, instead of using the word "localhost".
So, if you're developing locally, calling you app with your IP, try calling it on http://localhost!


------------
    
    
## Answer \#3

 Vote: 0

Created at 2021-11-15 02:32:45

------------

Unlike @cslotty, in my case I actually had to change my URL from 'localhost' to '127.0.0.1' for it to work. My frontend is in React and the backend in Laravel 8.


------------
    
    
## Answer \#4

 Vote: 0

Created at 2022-06-09 15:29:30

------------

I faced this issue. I found the solution in Laravel document itself.
We can add `$csrf` after the form element
```
<form method="POST" action="/profile">
@csrf

  //input fields here
</form>
```



------------
    
    