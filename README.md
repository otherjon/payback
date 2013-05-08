Payback
=======

The payback script tracks a series of group expenses and payments, and
figures out who owes how much to whom.  The general principle is that
"the pot" pays for group events, and people owe money to (and pay money to)
the pot.

Example: Alice, Bob, Carol, and Dave have a group dinner costing $60 (and
they decide to split the cost evenly).  Alice pays $40 and Bob pays $20,
and later they try to figure out who owes what.  The line item looks like
this:

    Item: Dinner with the gang ("Dinner")
    Owe: Alice, Bob, Carol, Dave      Paid: Alice(40.00), Bob(20.00)

"The pot" paid $60.  Everyone owes equally, so everyone owes $15.  Carol and
Dave didn't pay anything, so they each owe the pot $15.  Bob paid $20 but
only owed the pot $15, so the pot owes him $5.  Alice paid $40 but only owed
the pot $15, so the pot owes her $25.  Carol and Dave pay the pot their $30,
which is then distributed to Alice and Bob.

INPUT FILE SYNTAX
 * An optional line-item detailed name, with an optional short name.  (Note
   that the second example doesn't have a separate short name.)<br>
    `Item: Long detailed line-item name ("Short Name")`<br>
    `Item: Quick Item`

 * The list of people who owe money for the line item, with optional
   hard-coded amounts that they owe, e.g. if they don't owe an equal
   share.  (All people who don't owe a hard-coded amount will split the
   remaining balance equally.)<br>
    `Owe: Alice, Bob(100.00), Carol(50.00), Dave`<br>
   (In the above example, Bob owes $100, Carol owes $50, and Alice and
    Dave split the remainder equally.)

 * The list of people who paid for the line item, and how much<br>
    `Paid: Alice(100.00), Bob(200.00)`<br>
   (must be on the same line as the "Owe:" segment)

 * blank lines are ignored
 * lines starting with # are ignored
 * lines starting with "Comment:" are printed out but otherwise ignored

 * See `sample.data` for an example.