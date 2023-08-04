Flask-Babel
Flask-Babel is an extension to Flask that adds i18n and l10n support to any Flask application with the help of babel, pytz and its own copy of speaklater. It has built-in support for date formatting including timezones, as well as a very simple and friendly interface to gettext translations.

Installation
Install the extension from PyPi:

$ pip install Flask-Babel
Please note that Flask-Babel requires Jinja >=2.5. If you are using an older version you will have to upgrade or disable the Jinja support (see configuration).

Configuration
To get started all you need to do is to instantiate a Babel object after configuring the application:

from flask import Flask
from flask_babel import Babel

app = Flask(__name__)
babel = Babel(app)
To disable jinja support, include configure_jinja=False in the Babel constructor call. The babel object itself can be used to configure the babel support further. Babel has the following configuration values that can be used to change some internal defaults:

BABEL_DEFAULT_LOCALE

The default locale to use if no locale selector is registered. This defaults to 'en'.

BABEL_DEFAULT_TIMEZONE

The timezone to use for user facing dates. This defaults to 'UTC' which also is the timezone your application must use internally.

BABEL_TRANSLATION_DIRECTORIES

A semi-colon (;) separated string of absolute and relative (to the root_path of the application object) paths to translation folders. Defaults to translations.

BABEL_DOMAIN

The message domain used by the application. Defaults to messages.

It can also be a semi-colon (;) separated string of different domains for each of the translation directories, eg:

BABEL_TRANSLATION_DIRECTORIES=/path/to/translations;/another/path/
BABEL_DOMAIN=messages;myapp

from flask import g, request

def get_locale():
    # if a user is logged in, use the locale from the user settings
    user = getattr(g, 'user', None)
    if user is not None:
        return user.locale
    # otherwise try to guess the language from the user accept
    # header the browser transmits.  We support de/fr/en in this
    # example.  The best match wins.
    return request.accept_languages.best_match(['de', 'fr', 'en'])

def get_timezone():
    user = getattr(g, 'user', None)
    if user is not None:
        return user.timezone

app = Flask(__name__)
babel = Babel(app, locale_selector=get_locale, timezone_selector=get_timezone)
