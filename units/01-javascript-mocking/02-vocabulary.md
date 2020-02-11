# Vocabulary

- **Mock:** An object that simulates the data and functionality of a dependency. When used in testing, mocks simulate needed pieces without requiring the real objects to be integrated.

- **Mock (verb):** The act of using a mocked object to fill a requirement in a test.

- **Stub:** A simple mock that holds static data (JSON) needed for some operation. Stubs are most often used when mocking calls to a database or API.

- **Spy:** A mocked function that allows tracking of the calls to that function, such as number of calls and the arguments passed with calls.

- **Constructor Injection:** A technique that involves using constructor parameters to receive the required dependencies of the class or object. This does not have to be the only constructor but it provides a mechanism to supply dependencies instead of the object relying on external dependencies it does not control.

