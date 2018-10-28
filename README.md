# Pagespeed issue with picture elements

The following project is a showcase of the issue Google Pagespeed has with HTML picture elements.

## Example 1 - Using picture elements

### Code

index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, 
       maximum-scale=1.0, user-scalable=no"/>
    <meta charset="UTF-8">
    <title>Pagespeed using picture</title>
    <style>
        body{font-size: 100%;padding: 1em;}img{max-width: 100%;}
    </style>
</head>
<body>
    <picture>
        <source srcset="images/image-l-146a86e4.jpg" 
           media="(min-width: 801px) and (max-width: 1024px)" />
        <source srcset="images/image-m-a006929e.jpg" 
           media="(min-width: 321px) and (max-width: 800px)" />
        <source srcset="images/image-s-2313f2e3.jpg" 
           media="(max-width: 320px)" />
        <img src="images/image-xl-332b4582.jpg" alt="" />
    </picture>
    ...
    <link rel="stylesheet" href="styles/pagespeed.css">
</body>
</html>
```
pagespeed.css (formatted version)
```
body {
    font-size: 100%;
    padding: 1em;
}

img {
    max-width: 100%;
}
```

### Test results

* [Google Pagespeed](https://developers.google.com/speed/pagespeed/insights/?hl=en&url=http%3A%2F%2Fdesign.humml.eu%2Fsandbox%2Fpagespeed%2Findex.html)

## Example 2 - Using background images instead

index2.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"/>
    <meta charset="UTF-8">
    <title>Pagespeed using background image</title>
    <style>
        body{font-size:100%;padding:1em}img{max-width:100%}#banner{background:url(images/image-xl-332b4582.jpg) center no-repeat #efefef;background-size:cover;height:1200px}@media (min-width:801px) and (max-width:1024px){#banner{background-image:url(images/image-l-146a86e4.jpg);height:683px}}@media (min-width:321px) and (max-width:800px){#banner{background-image:url(images/image-m-a006929e.jpg);height:500px}}@media (max-width:320px){#banner{background-image:url(images/image-s-2313f2e3.jpg);height:181px}}
    </style>
</head>
<body>
    <div id="banner"></div>
    ...
    <link rel="stylesheet" href="styles/pagespeed2.css">
</body>
</html>
```

pagespeed2.css (formatted version)
```
body {
    font-size: 100%;
    padding: 1em
}

img {
    max-width: 100%
}

#banner {
    background: url(../images/image-xl-332b4582.jpg) center no-repeat #efefef;
    background-size: cover;
    height: 1200px
}

@media (min-width: 801px) and (max-width: 1024px) {
    #banner {
        background-image: url(../images/image-l-146a86e4.jpg);
        height: 683px
    }
}

@media (min-width: 321px) and (max-width: 800px) {
    #banner {
        background-image: url(../images/image-m-a006929e.jpg);
        height: 500px
    }
}

@media (max-width: 320px) {
    #banner {
        background-image: url(../images/image-s-2313f2e3.jpg);
        height: 181px
    }
}
```

### Test results

* [Google Pagespeed](https://developers.google.com/speed/pagespeed/insights/?hl=de&url=http%3A%2F%2Fdesign.humml.eu%2Fsandbox%2Fpagespeed%2Findex2.html)
