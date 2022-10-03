# ts-errors
## Guide to Handling Errors

Ways to handle errors:

* Return `null`
  * Doesn't tell you _why_ something failed
  * It's awkward to check for null every time
* Throw exceptions
  * Tells you why something failed
  * Types can't ensure that all exceptions are accounted for
* Return exceptions and make return type a union of the happy path and each exception
  * Tells you why something failed
  * Forces developers to handle exceptions
  * Verbose
* `Option` type
  * Allow you to chain operations if one of them might fail
  * Doesn't tell you _why_ something failed
  * Not interoperable with code that doesn't use monads

Using never?
