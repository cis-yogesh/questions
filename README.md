## LeafLink

### Instructions
This file is a markdown document which has some basic technical questions to assess your fit. Please provide your solutions to the problems within this markdown file. A recommended markdown editor is [Mou](http://25.io/mou/).

**Why LeafLink**

##### What interests you about LeafLink from an industry standpoint and our proposed tech offerings?

>Do not know about LeafLink, I didn't use this type of technology

**Linux**

##### How do I reconnect to an existing screen or tmux session named 'leaflink'?

> tmux attach -t leaflink

##### How would I "follow" the output of a server log named 'access.log'?

```tail -f access.log```

##### How would I remove all files in a directory that start with an 'a' and have a '.jpg' extension?

```rm -rf a*.jpg```

##### How would I see all running processes and memory they consume?

```ps aux or top ```

##### How would I combine the following files: '1.log', '2.log', '3.log' into a single file named 'master.log'?

```cat 1.log 2.log 3.log >master.log```

**Database**

##### What is a database index and when is it wise to build an index?

> database index is a B- tree that stores the values for a specific column in a table

```CREATE INDEX name_index ON Table (value)```

Table Name: 'pets'

| owner |      pet      | age |
|-------|:-------------:|----:|
| bob   |      dog      |  3  |
| cindy |      cat      |  5  |
| lisa  |      cat      |  7  |
| tony  |      fish     |  1  |


##### Write a query to return all unique pets in the 'pets' table.

> select distinct pet from pets

##### Write a query to return the oldest cat owner in the 'pets' table.

> select * from pets where pet='cat' order by age LIMIT 1

##### Write a query to return the average age of all cats and dogs in the 'pets' table.

> SELECT AVG(age) as avgAge FROM pets GROUP BY pet HAVING pet IN ('cat','dog');

**Python**
##### What is your favorite python module and why?

> numpy, pandas and pyspark 


##### Write python code to return an iterable which contains all unique numbers in the list [1, 3, 4, 5, 2, 2, 1, 4].

```
li = [1, 3, 4, 5, 2, 2, 1, 4]
result = set(li)
```

##### Write python code to find the largest number in [1, 3, 4, 5, 2, 2, 1, 4].

```
li = [1, 3, 4, 5, 2, 2, 1, 4]
result = max(li)

```


##### Write python code to return common elements between l = [1, 'A', 3, 5] and p = [8, 3, 5, 'A'].

> result = list(set(l) & set(p)) 

##### Write python code to sort the following from highest to lowest [1, 3, 4, 5, 2, 2, 1, 4].

>result = li.sort(reverse=True)


**Django**

##### Write a formal Django model for a typical 'Blog' entry.

```
class BlogCategory(models.Model):
    """
    Blog category
    """
    parent = models.ForeignKey('self', verbose_name=_('parent'), null=True, blank=True)
    date_created = models.DateTimeField(_('created at'), auto_now_add=True)
    date_modified = models.DateTimeField(_('modified at'), auto_now=True)

class Blog(models.Model):
    """
    Blog post
    """
    author = models.ForeignKey(settings.AUTH_USER_MODEL, related_name='blogs')

	title=models.CharField(_('title'), max_length=255),
	slug=models.SlugField(_('slug'), blank=True, db_index=True),
	abstract=HTMLField(_('abstract'), blank=True, default=''),
	meta_description=models.TextField(verbose_name=_('post meta description'),
			                      blank=True, default=''),
	meta_keywords=models.TextField(verbose_name=_('post meta keywords'),
			                   blank=True, default=''),
	meta_title=models.CharField(verbose_name=_('post meta title'),
			                help_text=_('used in title tag and social sharing'),
			                max_length=255,
			                blank=True, default=''),
	post_text=HTMLField(_('text'), default='', blank=True),

    date_created = models.DateTimeField(_('created'), auto_now_add=True)
    date_modified = models.DateTimeField(_('last modified'), auto_now=True)
    date_published = models.DateTimeField(_('published since'),
                                          default=timezone.now)
    date_published_end = models.DateTimeField(_('published until'), null=True,
                                              blank=True)
    publish = models.BooleanField(_('publish'), default=False)
    categories = models.ManyToManyField('djangocms_blog.BlogCategory', verbose_name=_('category'),
    enable_comments = models.BooleanField(verbose_name=_('enable comments on post'),
                                          default=get_setting('ENABLE_COMMENTS'))

```

##### Using the Django ORM how would you find all owners in the 'pets' table above who have a cat older than 1? Assume the Model name is "Pet".

```
pets = Pet.objects.filter(pet='cat', age__lt=1)

```

##### Render your query set above using Django template syntax as an HTML Table.

```
<table>
{% for pet in pets %}
	<tr>
		<td>{{pet.owner}}</td>
		<td>{{pet.pet}}</td>
		<td>{{pet.age}}</td>
	</tr>
{% endfor %}
</table>

```


**API**

##### Write python code to print all pet owner names for the following 'JSON web service'.
<http://dpaste.com/1V5NTFH.txt>

`[solution]`

**Javascript**

##### What is the DOM?

>DOM stands for Document Object Model and is a mechanism for representing and interacting with HTML.


Write a jQuery selector to select all list items that have 'cat' as a class.


```<ul>
    <li class="dog">dog</li>
    <li class="cat">cat</li>
    <li class="fish">fish</li>
    <li class="cat">cat</li>
</ul>
```

> $('ul li.cat')

