Account data storage:

An accounts data storage is a storage, associated with an account, of data records.

Each account has a single account data storage.

The size of an accounts data storage is unlimited.



An account data storage record:

An account data storage record is a data record that has a key-value format.

The key is a unique string.

The value is the data of one of the types:

    string
    boolean
    integral
    array of bytes




Adding records:

Records are added to an account data storage using a data transaction or an invoke script transaction.

The maximum size of a single record is 32 kilobytes
for data transaction and 5 kilobytes for invoke script transaction.


Editing records:

The value of a record can be rewritten using a data transaction or an invoke script transaction.

The key of a record cannot be rewritten.



Deleting records:

    From version 1.2.0, it is possible to delete account data storage records. This functionality becomes available after activation of feature #15 “Ride V4, VRF, Protobuf, Failed transactions” on the node. 

Deleting records is implemented by

    data transaction
    DeleteEntry structure

Deleting a record is performed by key.
