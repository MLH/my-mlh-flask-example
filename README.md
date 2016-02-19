# MyMLH Flask Example

This is an example application that uses Flask, SQLAlchemy, and rAuth to
authenticate users for MyMLH.

## Setup

These are the steps to get the app up and running:

#### Step 1. Create a Virtual Environment and install Dependencies

Create a new Virtual Environment for the project and source it.  If you don't have Virtaul Environment yet, you can find installation [instructions here](https://virtualenv.readthedocs.org/en/latest/).

```
$ virtualenv venv
$ source venv/bin/activate
```

Next we need to install the project dependencies, which are listed in `requirements.txt`.

```
(venv) $ pip install -r requirements.txt
```

#### Step 2. Create an app on MyMLH

Head over to [http://my.mlh.io/](http://my.mlh.io/) and register a new application.  You'll need to specify a callback url, which should be something like:

```
http://localhost:5000/callback/mlh
```

The default port for flask apps is `5000`, but you may need to update this if your setup uses a different port or if you're hosting your app somewhere besides your local machine.

#### Step 3. Update app.py and run the Server

Open up app.py with your favorite text editor and insert the MyMLH App ID and Secret you got once you setup your app.

```python
app.config['OAUTH_CREDENTIALS'] = {
    'mlh': {
        'id': '[INSERT MyMLH APP ID]',
        'secret': '[INSERT MyMLH SECRET]'
    }
}
```

Now we're ready to start our server which is as simple as:

```
(venv) $ python app.py
```

## Credit

This sample is built off of the [Flask OAuth Example](https://github.com/miguelgrinberg/flask-oauth-example) by Miguel
Grinberg and retains his MIT License.
