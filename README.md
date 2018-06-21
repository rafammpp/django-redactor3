# Django-redactor3
This not include redactor js or css files.

## Settings
All redactor settings in [imperavi redactor](https://imperavi.com/redactor/docs/settings/)
example:
REDACTOR_OPTIONS = {}
REDACTOR_OPTIONS['fileUpload'] = 'uploads/'

Note:
Boolean values must be quoted (this fix compatibility errors with js booleans values). Like this:
```Python
class Article(models.Model):
	title = RedactorField(redactor_options={'pastePlainText': 'true', 'linebreaks': 'True'})
```

### Other django-side settings with default values:

REDACTOR_FILE_STORAGE = 'django.core.files.storage.DefaultStorage'
REDACTOR_UPLOAD = 'redactor/'
REDACTOR_UPLOAD_HANDLER = 'redactor.handlers.SimpleUploader'
REDACTOR_AUTH_DECORATOR = staff_member_required

### Set options per field

You can set options per field in models, example:

```Python
class Article(models.Model):
	title = RedactorField(redactor_options={'pastePlainText': 'true', })
	text = RedactorField(verbose_name=u'Text',
						 null=True,
						 blank=True,
						 redactor_options={'minHeight': '300px', 'maxHeight': '800px', }
						 )
```