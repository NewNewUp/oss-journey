PR #3304. Tool schemas listed enum CONSTANT NAMES ("LOW") while the Jackson
conversion path accepted the @JsonProperty RENAMED values ("低"). Every call
failed. Root cause: the victools schema generator was built without
FLATTENED_ENUMS_FROM_JSONPROPERTY/_FROM_JSONVALUE.

Fix: enable the two options so schema and codec agree. The deeper lesson: when
two subsystems serialize the same data, the contract must be one line of code
apart — here a single module options list.
