# Accounts

Accounts represent your customers in our system. We specifically used the more
generic term "account" because your customer may be a user, or team, or company
– or something else entirely.

To put it another way: If you want to give them access to writing their own code
in your app, they need an account to represent them, so that your app and
Lateral.run have a shared understanding of the customer in question.

An account is just a string (or anything that can be coerced to a string) that
uniquely identifies them, which is usually the primary key in your database. For
example, if your customer is a user, you have something like a `users.id` field
that's an auto-incrementing integer or UUID. That's what you would use to
represent them in Lateral.run.

## Creating an Account

We auto-create accounts when we see a new one referenced in an
[Authentication](docs/authentication.md) token (the `sub` field) for the first
time. So, for example, the first time they view the embedded code editor in your
frontend, we create an account to represent them on our side. You don't have to
explicitly create new accounts for your customers before they can use
Lateral.run.

That said, you can manually create one by heading to the _Accounts_ section of
Lateral.run and looking for the _New_ button.

## Namespacing

You can represent more than one type of customer by namespacing the identifier
you use. For example, if you want to allow both users and teams to write their
own code in your app, you can use something like `users/{{ID}}` and
`teams/{{ID}}` to uniquely identify them. (There's nothing special about the
terms or delimiter (`/`) used in this example, so feel free to use whatever you
prefer.)
