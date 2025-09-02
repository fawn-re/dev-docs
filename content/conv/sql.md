+++
date = '2025-08-21T14:37:07-06:00'
draft = true
title = 'SQL'
+++

# SQL Coding Conventions

Please keep the following coding conventions in mind when writing SQL.

{{< h2 title="Naming" >}}

Use uppercase for reserved words. Use snake case for table and column names.

```sql
-- good
SELECT * FROM foo.bar_baz
WHERE quux = 1;

-- bad
select * from Foo.BarBaz
where Quux = 1;
```

{{< h2 title="Spacing" >}}

Use hard tabs for indentation. Use Unix-style line endings (LF) rather than Windows-style (CRLF). Lines must not have unnecessary trailing whitespace.

The packet from 2021-06-15 includes some dubious guidelines regarding spacing that to my knowledge are not enforced:

> - new lines for reserved words e.g. (JOIN, ON, AND, OR, GROUP BY..)
> - new lines for every item in select statement
> - new lines allowed for SQL functions in SELECT as long as there is indentation e.g.(GROUP_CONCAT, CONCAT, IF, CASE)
> - indentation for ON after a JOIN
> - chained functions should line up with keywords
> - select columns should line up with keywords
