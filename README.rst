================
Django admin SSO
================
Django admin SSO lets users login to a django admin using an openid provider. It
then looks up the email address of the new user and looks up the rights for him.

Installation
------------

1. Make sure you have a working django project setup.
2. Install django-admin-sso using pip::

    pip install django-admin-sso

3. Add ``admin_sso`` to ``INSTALLED_APPS`` in your ``settings.py`` file::

    INSTALLED_APPS = (
        ...
        'admin_sso',
        ...
    )

4. Add the django-admin authentication backend::

    AUTHENTICATION_BACKENDS = (
        'admin_sso.auth.DjangoSSOAuthBackend',
        'django.contrib.auth.backends.ModelBackend',
    )

5. Run syncdb to create the needed database tables.

6. Log into the admin and add an Assignment.


Assignments
-----------
Any Remote User -> Local User X
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Select Username mode "any".
* Set Domain to your authenticating domain.
* Select your local user from the User drop down.


Remote User -> Local User
~~~~~~~~~~~~~~~~~~~~~~~~~
* Select Username mode "matches" *or* "don't match".
* Set username to [not] match by.
* Set Domain to your authenticating domain.
* Select your local user from the User drop down.


Test report/coverage
--------------------

Test results:

    ......
    Ran 6 tests in 0.104s
    
    OK

Coverage report:

    Name                         Stmts   Miss  Cover   Missing
    ----------------------------------------------------------
    admin_sso/__init__              16      2    88%   7-8
    admin_sso/admin                 19     19     0%   1-34
    admin_sso/auth                  65     13    80%   5-6, 19-22, 27, 37-39, 51, 54-55
    admin_sso/default_settings      10      0   100%   
    admin_sso/models                47      7    85%   5-7, 28, 43, 46-47
    admin_sso/store                 68     68     0%   31-132
    admin_sso/views                 57     57     0%   1-79
    ----------------------------------------------------------
    TOTAL                          282    166    41%   
