# Categories Class

```php
# filename: Categories.class.php
# location: inc/lib/
# package: GeniXCMS
# since: 0.0.1
# author: Puguh Wijayanto (metalgenix.id)
# copyright: 2014-2024 Puguh Wijayanto
# license: MIT License
```

!!! info
    This Documentation is still need improvement.

This class is to manage the **Categories**. This category structure is very simple. 

An improvement probably added in the future. Below are the explanation each method at the Categories Class.


## Dropdown Method

Usage : `#!php echo Categories::dropdown(array $vars);`

Return: `#!php string`

This method to create an automatic dropdown options from available categories at the database. It means we can create dropdown so easy, just fill in the parameters and a **select input** created automatically.

Example:

```php
$vars = array(
             'name'      =>  'catname',
             'parent'    =>  'parent',
             'order_by'  =>  '',
             'sort'      =>  'ASC',
           )
echo Categories::dropdown($vars);
```

That methods calls will create output like this.

```html
<select name="catname" class="form-control">
	<option></option>
	<option value="1">Category Name</option>
	...
</select>
```

Explanation:

- **name**, this is the name  of the select input.
- **parent**, this is the parent of the category you want to show. No parent or *empty* means all categories will shows up. 
- **order_by**, this is how you want the category ordered by. Available columns are : `id`, `name`, `slug`, `parent`, `desc` default is `id`
- **sort**, this is the options how your categories sorted, Ascending `ASC`, or Descending `DESC`. Default is `ASC`


See also:

- [Db::result()](db.class.md)

  

## Lists Method

Usage : `#!php echo Categories::lists(array $vars)`

This method will show the list of the **Categories** and **Subcategories** with the unordered list markup. 

example: 

```php
$vars = array(
             'parent'    =>  'parent',
             'order_by'  =>  '',
             'sort'      =>  'ASC',
           )
echo Categories::lists($vars);
```

Explanation:

<!-- - **name**, this is the name  of the select input. -->
- **parent**, this is the parent of the category you want to show. No parent or *empty* means all categories will shows up. 
- **order_by**, this is how you want the category ordered by. Available columns are : `id`, `name`, `slug`, `parent`, `desc` default is `id`
- **sort**, this is the options how your categories sorted, Ascending `ASC`, or Descending `DESC`. Default is `ASC`

See also:

- [Db::result()](db.class.md)


## Name Method

Usage: `#!php echo Categories::name(int '$id');`

Return: `#!php string`

This method will get the name of Category for the specific ID.

example:

we have a list of categories with sample below :


| ID  | Name     |
|-----|----------|
| 1   | News     |
| 2   | Article  |


```php
$catName = Categories::name(1);
echo $catName;
```

this will output `News`.

```php
$catName = Categories::name(2);
echo $catName;
```

this will output `Article`.

See also:

- [Db::result()](db.class.md)
  

## getParent Method

Usage: `#!php echo Categories::getParent(int '$id');`

Return: `#!php int`

This is to get the **Parent ID** of a speicific **Category ID**.

example:

we have a list of categories with sample below :



| ID | Name    | Parent |
|----|---------|--------|
| 1  | News    | 0
| 2  | Article | 0
| 3  | Latest  | 1


```php
$parent = Categories::getParent(3);
echo $parent;
```

this will output `1`.

See also:

- [Db::result()](db.class.md)



## Delete Method

Usage: `#!php Categories::delete(int '$id');`

Return: `#!php bool`

This method will delete a Category with a specific ID.

See also:

- [Db::result()](db.class.md)


## Type Method 

Usage: `#!php Categories::type(int '$id');`

Return: `#!php string`

This method will query the categories table and find the specific `id` and output the **type of the category**.

example:

we have a list of categories with sample below :



| ID | Name    | Parent | Type
|----|---------|--------|------
| 1  | News    | 0      | post
| 2  | Article | 0      | post
| 3  | Latest  | 1      | post


```php
$type = Categories::type(3);
echo $type;
```

this will output `post`.

See also:

- [Db::result()](db.class.md)



