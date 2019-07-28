### mezzanine
---
http://mezzanine.jupo.org/

https://github.com/stephenmcd/mezzanine

```
{% load mezzanine_tags %}
<html>
</html>

```

```sh
pip instal mezzanine
mezzanine-project myproject
cd maproject
python manage.py createdb
python manage.py runserver
```

```py
from mezzanine.utils.admin import SingletonAdmin
from .models import SiteAlert

class SiteAlertAdmin(SingletonAdmin):
  pass
admin.site.register(SiteAlert, SiteAlertAdmin)

from django.db import models
class SiteAlert(models.Model):
  message = models.TextField(blank=True)
  class Meta:
    verbose_name_plural = "Site Alert"

from django.utils.safestring import mark_safe
from markdown import markdown

def markdown_filter(content):
  """
  """
  return mark_safe(markdown(content))
RICHTEXT_FILTERS = (
  "myproj.filter.markdown_filter",
)

from django.contrib import admin
class BlogCategoryAdmin(admin.ModelAdmin):
  """
  """
  fieldsets = ((None, {"fields": ("title",)}),)
  def has_module_permission(self, request):
    """
    """
    for (name, items) in settings.ADMIN_MENU_ORDER:
      if "blog.BlogCategory" in items:
        return True
    return False
```


