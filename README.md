Break the captcha + PIN code, as part of a [Blacklight](https://blacklight.ai) challenge: disable a security camera.

Per default, only the case of not incorrect PIN and not incorrect captcha, i.e. what is likely to be the correct PIN+captcha combination, will be printed. For displaying the logs, run with flag  `-printlog=true`

As part of the [GopherAcademy Advents Calendar series](https://blog.gopheracademy.com/advent-2017/tensorflow-and-go/) I wrote a more detailed explanation of the code.

This code is also the base for [my talks on the use of TensorFlow with Go](https://github.com/Pisush/Public-Speaking#talks) from 2018, e.g. at [Gotham Go](http://gothamgo.com/speakers/index).


## Running the service

Build the image.

```
$ docker build -t localhost/recognition .
```

Run service in a container.

```
$ docker run -p 8080:8080 --rm localhost/recognition
```

Call the service.

```
$ curl localhost:8080/recognize -F 'image=@./cat.jpg'
{
  "filename": "cat.jpg",
  "labels": [
    { "label": "tabby", "probability": 0.45087516 },
    { "label": "Egyptian cat", "probability": 0.26096493 },
    { "label": "tiger cat", "probability": 0.23208225 },
    { "label": "lynx", "probability": 0.050698064 },
    { "label": "grey fox", "probability": 0.0019019963 }
  ]
}
```