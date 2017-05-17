Steps to reproduce segmentation fault

```
docker build -t debug_raven:latest .
docker run --rm -it debug_raven sh
```

Inside container:

```
export FLASK_APP=service/__init__.py
export FLASK_DEBUG=1
flask run

 * Serving Flask app "service"
 * Forcing debug mode on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with stat
Segmentation fault
```

If the following line is removed from `service/__init__.py` then the segmentation fault goes away:

`from raven.contrib.flask import Sentry`
