# Events

Events represent the points in your app where you want to allow your customers
to run their own code.

Let's say your app is a CRM. You might define the following events:

- _New Contact_
- _New Email_
- _Enrich Contact_

There's no "right way" to define events for your app – since everyone is
different in the functionality they want to enable – so don't spin your wheels
too much trying to define them all up-front. Start with one or two, then add
more as they make sense.

## Creating an Event

To create an event, head to the _Events_ section of Lateral.run and look for the
_New_ button. You'll be asked for three pieces of information:

- _Identifier_ is the unique identifier you'll use to refer to the event in your
  code. For example, `contacts.new` or `users.edit`. See below for our
  recommendation on naming these.
- _Name_ is the human readable name for the event that's displayed to your
  customers. For example, _New Contact_ or _Edit User_.
- _Example Data_ is a JSON object that represents what might be sent to your
  customer's code. It's automatically populated in the code editor for
  convenience when testing.

## Recommendation on Naming

Naming things can be tricky, so here's our recommendation when naming
identifiers: start with the most general _thing_ on the left, and progress to
the most specific _thing_ on the right, with a delimiter in between each
_thing_.

The examples above follow this pattern. Take for example `contacts.new`.
`contacts` is the most general _thing_, while `new` is a more specific action
that can be taken on a contact. `.` is used as the delimiter. This can, of
course, be expanded to more than just two _things_ – just follow the pattern.
