# Viggoscrape

Python library for scraping *[Viggo](http://viggo.dk/)* assignments by interacting with the [Viggoscrape API](https://viggoscrape.xyz/).

>The API is designed for **danish** users, and time will be adjusted to the **CET** timezone.

## Quickstart

### Information syntax

To use Viggoscrape, you need to provide it with login info in the form of a dictionary.

The login info uses 3 pieces of information:
-  Subdomain
-  Username
-  Password

For your subdomain, specify only the subdomain, like this:

`subdomain-example`

And not like this:

`subdomain-example.viggo.dk`

### Usage example

Let's try this out! We'll import the library, give it the required info and print the result, catching any error that may happen.

```python
from viggoscrape import get_assignments

try:
    data = get_assignments(
        {
            "subdomain": "example-subdomain",
            "username": "johndoe@gmail.com",
            "password": "Password1234"
        }
    )
    print(data)
except Exception as e:
    print(e)
```

Our output would look something like this:
```json
{
    "subject": ["English", "Math"],
    "time": ["31. aug 12:00", "2. sep 08:55"],
    "description": ["Read pages 30 and 31", "Finish A, B and C"],
    "author": ["28. aug 11:25 by John Doe", "31. aug 15:30 by Peter Anker"],
    "files": ["None", "example.com/algebra.pdf"],
    "file_names": ["None", "Intro to algebra"],
    "url": ["https://example-subdomain.viggo.dk/Basic/HomeworkAndAssignment/Details/1234/#modal", "https://example-subdomain.viggo.dk/Basic/HomeworkAndAssignment/Details/1235/#modal"]
}
```
Or if something went wrong and the provided subdomain is invalid:
```python
"Invalid subdomain"
```
Or if the password or username is misspelt:
```python
"Invalid credentials"
```

Now, you can do anything you want with this newfound data, like save it to a json file, create an embed for your [discord bot](https://github.com/nangurepo/fessor), or any other purpose. Just use the same index on all lists and the data should match.