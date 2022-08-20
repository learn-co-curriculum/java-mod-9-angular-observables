# Observables

## Learning Goals

- Give an overview of observables.

## Angular Observables

Angular Observables are a complex subject that is beyond the scope of this
course for in-depth exploration. That said, we encountered them for the first in
the previous section and we will use them again for routing, so we should have a
quick overview here:

1. Observables are a mechanism for communication in Angular, including between
   components, between components and services and between services and their
   external dependencies (such as the API endpoints we integrated with in the
   previous section)
2. When a method returns an Observable, it returns from that call immediately
   without waiting for the work associated with the method call to be completed.
3. In the context of HTTP calls, that means our application code doesn't have to
   "block wait" until a remote server responds to continue with its local work
4. Instead, we have to register a "callback" function with the Observable. That
   function will be called when the actual work of the method is completed
5. This is called "asynchronous" communication:
   1. The caller makes a call
   2. The target receives the call and initiates work
   3. Regardless of how long it takes to complete the work, the target returns
      an initial response (this is the Observable)
   4. This initial response does not indicate that the work has completed and
      contains no data regarding the completion or status of the work
   5. When the target finishes the work, it notifies anyone who subscribed to
      the Observable and returns the data associated with the completion of the
      work
6. Calling a method that returns an Observable does not execute the code of the
   Observable - Angular tracks who is subscribed to the Observable and if no one
   is subscribed, i.e. no one is interested in the result of the work, Angular
   will not perform the work.

Here is a high level visual representation of the flow of a call to an
Observable:

> Note: this is a simplified representation of Observables for `HTTP` calls -
> for other types of Observable, there might be more than one callback to the
> caller because Observables have the ability to generate multiple events for
> their subscribers.

![Angular Observables Flow](https://curriculum-content.s3.amazonaws.com/java-mod-8/ng-observables-flow.png)
