# testable-architecture-toolkit.net
Provides .Net Source Generators to minimize boilerplate code required for adhering to a SOLID testable software architecture.

## Planned Source generators

### Complete interface for class

Generates an interface for an annotated class which contains all public members of the class.
If an interface is implemented just to make the class mockable in unit tests, this source generator should make it easier.

### Wrapper for class

Generates a wrapper class for another class that contains the same public/protected methods as the original class and forwards method calls to an instance of the original class. The instance of the original class has to be provided in the constructor of the wrapper.

Additionally, the wrapper class implements an interface, making it mockable.
By using the wrapper instead of the original class, the original class mockable in unit tests, even when the original class does not implement an interface. 

### Factory for class constructors

Generates a class that contains a factory method for each constructor of another class that simply wraps the constructor. 
Additionally it implements an interface to make the factory mockable.

A developer using the source generator should be able to specify an interface that is implemented by the original class, which is be returned by the factory methods instead of the original class type.

## Planned analyzers

### Do not inherit from classes that define custom methods

Inheriting from classes that define custom methods means, that the custom methods on the base class can be used by methods implemented on the inheriting class. 
This strong coupling should be avoided because base class methods can not be mocked in child class unit tests, meaning that the child class logic can only be asserted indirectly and unit tests can potentially become much more complex.

