Chloroform_HydrogenRenderer
===========
2019-04-18



A basic renderer for [Chloroform](https://github.com/lingtalfi/Chloroform).


This is part of the [universe framework](https://github.com/karayabin/universe-snapshot).


Install
==========
Using the [uni](https://github.com/lingtalfi/universe-naive-importer) command.
```bash
uni import Ling/Chloroform_HydrogenRenderer
```

Or just download it and place it where you want otherwise.






Summary
===========
* [Chloroform_HydrogenRenderer api](https://github.com/lingtalfi/Chloroform_HydrogenRenderer/blob/master/doc/api/Ling/Chloroform_HydrogenRenderer.md) (generated with [DocTools](https://github.com/lingtalfi/DocTools))
* [What is it?](#what-is-it)
    * [Implemented fields](#implemented-fields)
    * [Implemented js validators](#implemented-js-validators)
* [How to use](#how-to-use)
* [Creating other renderers](#creating-other-renderers)
* [History Log](#history-log)





What is it?
============

This is my first [Chloroform](https://github.com/lingtalfi/Chloroform)renderer attempt.

It basically renders a Chloroform form.



It also provides js validation for free.

The js validation is based on the [Chloroform validators](https://github.com/lingtalfi/Chloroform#the-available-validators).

This means you don't have to type a single line of javascript, the HydrogenRenderer takes care of that for you.  



I created a [css prototype](http://lingtalfi.com/universe/Ling/Chloroform_HydrogenRenderer/prototype) before I implemented the renderer (it's not functional, just pure css design, no js layer either).
It should give you a pretty good idea of how the renderer looks like.






Implemented fields
-------------

The Hydrogen renderer can render the following fields:

- StringField
- TextField
- NumberField
- HiddenField
- CSRFField
- ColorField
- DateField
- TimeField
- DateTimeField
- SelectField
- CheckboxField
- RadioField
- FileField
- PasswordField


See the [Chloroform available fields](https://github.com/lingtalfi/Chloroform#the-available-fields) for the complete list of fields.


Implemented js validators
-----------

The Hydrogen renderer's js layer will handle the following validators:


- MinMaxCharValidator
- MinMaxNumberValidator
- MinMaxDateValidator
- MinMaxItemValidator
- MinMaxFileSizeValidator
- FileMimeTypeValidator
- RequiredValidator
- RequiredDateValidator
- PasswordConfirmValidator

See the complete [list of Chloroform validators here](https://github.com/lingtalfi/Chloroform#the-available-validators).





How to use
==============


You first need to import the assets.
The HydrogenRenderer depends on three assets:

- jquery (you can use a cdn for instance)
- the hydrogen.js file provided with this planet (must be called AFTER jquery)
- the hydrogen.css file provided with this planet 



Once the assets are imported, you instantiate the HydrogenRenderer with some options, and then call the render method.

For more details about the options, see the [HydrogenRenderer class](https://github.com/lingtalfi/Chloroform_HydrogenRenderer/blob/master/doc/api/Ling/Chloroform_HydrogenRenderer/HydrogenRenderer.md) documentation.


```php


// ...
$formArray = $form->toArray(); // $form = your Chloroform instance


// let's import the assets
?>
    <script
            src="https://code.jquery.com/jquery-3.4.0.min.js"
            integrity="sha256-BJeo0qm959uMBGb65z40ejJYGSgR7REI4+CW1fNKwOg="
            crossorigin="anonymous"></script>
    <script src="/js/hydrogen.js"></script>
    <link rel="stylesheet" href="/css/hydrogen.css">
<?php


// instantiate the renderer
$renderer = new HydrogenRenderer();

// then display the html code
echo $renderer->render($form->toArray()); 
```




Creating other renderers
===========

Now that this hydrogen renderer is created, I can see how much time would be saved by just copy pasting adapting
this renderer instead of re-creating a new renderer from scratch.

This is mainly due to the facts that:

- I created the renderer just after creating the Chloroform class, and so my mind was fully aware of all 
        the implementation details of the Chloroform system. And so the Hydrogen renderer fully embraces
        the Chloroform system as it should.
        
- I believe that more than 90% of the Hydrogen code could be re-used when creating a new renderer.
    For the HydrogenRenderer php class, all the html snippets will need to be changed, but the general organization can
    remain the same. My advice to the new renderer implementor would be: try to keep the logic behind the hydrogen
    renderer and you will be fine (as I said, there are some implementation details that you might miss if you go on your own
    and you're not fully aware of how Chloroform works).
    For the javascript layer, of course everything related to error injection would need to be reimplemented, but that's less
    than 10% of the file, and so you can reuse the validation logic entirely.
    
    
I created the Hydrogen renderer from scratch in three days.
By re-using the Hydrogen renderer as a basis for a new renderer, I might be able to minimize that time to one or two days (just a rough estimation of course,
depends on how complex the renderer is).
  

Note: if you just want a different look for the form, consider creating a new css file (instead of the hydrogen.css file). 
Depending on your css skills, you might get another look and feel quite easily.  




History Log
=============

- 1.0.0 -- 2019-04-18

    - initial commit