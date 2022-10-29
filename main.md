# WebAssembly as a functionfunction
## Description
Toolchain and plattform for pushing, managing and creating serverless functions compiled to Webassembly with the usage of wasmedge.

## Function
A function is based on Webassembly binary with the wasi extension. It is saved together wiht the sourc code inside an OCI image.
functions have three access modes:
- public: Accessible from anywhere
- private: Accessible for specified users inside the Function Group and functions inside the same Function Group
- internal: Only accessible by functions inside the same Function Group

All functions have an independent endpoint: \<baseUrl>/waaf/execution/\<functionGroup>/\<functionName>
The used method can be specified either while uploading the function or editing afterwards using the CLI or WebGUI.

## Funtion Group
Function Groups contain a seperate space for functions, which can be managed and used by users based on their role.
User roles:
- Admin: Can add and remove user
- Editor: Can add, remove and edit functions
- Reader: Can access information about functions, but can't edit them
- User: Can call the endpoint of the function but can't access any information
- Function Group: Function Groups can be added, so they can use private functions without authentication

For M2M purposes authentication with a secret is also possible

## Authentication
OpenID is used for Authentication.