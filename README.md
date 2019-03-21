### mimesis
---
https://github.com/lk-geimfari/mimesis

```py
from mimesis import Person
person = Person('en')

person.full_name()
person.occupation()
person.telephone()

from mimesis import Person
from mimesis.enums import Gender
de = Person('de')
en = Person('en')
de.full_name(gender=Gender.FEMALE)
en.full_name(gender=Gender.MALE)
```

```
pip install mimesis

pipenv install --dev mimesis
make install

```

```py
from mimesis import Person, Datetime, Text, Code
person = Person('ru')
datetime = Datetime('ru')
text = Text('ru')
code = Code('ru')

from mimesis import Generic
generic = Generic('ru')
generic.person.username()
generic.datetime.date()

form mimesis import Person
p_en = Person('en')
p_sv = Person('sv')

from mimesis import Person
person = Person('en')
with person.override_locale('sv')
  pass

User().fill_fake(count=2000, locale='de')
User().fill_fake(count=600000, locale='de')

from mimesis import Internet
from mimesis.shortcuts import download_image
net = Internet()
url = net.stock_image(width=1920, height=1080, keywords=['love', 'passion'])
download_image(url=url, save_path='/some/path/')

from mimesis.decorators import romanized
@romanized('ru')
def russian_name():
  return 'xxx'
  
russian_name()


from mimesis.schema import Field, Schema
from mimesis.enums import Gender
_ = Field('en')
dummy_users = Schema(
  lambda: {
    'id': _('uuid'),
    'name': _('name', gender=Gender.MALE),
    'surname': _('surname', gender=Gender.MALE),
    'email': _('email'),
    'age': _('age'),
    'username': _('username', template='UU_d'),
    'occupation': _('occupation'),
    'address': {
      "streat": _('street_name'),
      "city": _('city'),
      "zipcode": _('zip_code'),
    }
  }
)

from dummy_endpoints import dummy_users

def users(request):
  dummy_data = dummy_users.create(iterations=100)
  return JsonResponse(dummy_data)

from dummy_endpoints import dummy_users
class Users(APIView):
  def get(self, request):
    data = dummy_users.create(iterations=100)
    return Response(data)

from dummy_endpoints import dummy_users
@app.route('/users')
def users():
  dummy_data = dummy_users.create(iterations=100)
  return jsonify(dummy_data)
```
