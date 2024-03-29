# Lint Rules

We have lint rules to enforce the guidelines that have been set.

```yaml script

analyzer:
  errors:
    # treat missing required parameters as a errors (not a warning)
    missing_required_param: error
    # treat missing returns as a erros (not a warnings)
    missing_return: error

linter:
  rules:
    - always_declare_return_types
    - always_require_non_null_named_parameters
    - annotate_overrides
    - avoid_empty_else
    - avoid_types_as_parameter_names
    - avoid_unused_constructor_parameters
    - await_only_futures
    - camel_case_types
    - cancel_subscriptions
    - empty_constructor_bodies
    - always_declare_return_types
    - always_require_non_null_named_parameters
    - unnecessary_parenthesis
    - unnecessary_statements
    - unnecessary_brace_in_string_interps
    - unnecessary_const
    - unnecessary_new
    - unnecessary_null_aware_assignments
    - unnecessary_null_in_if_null_operators
    - prefer_const_constructors
    - prefer_const_declarations
    - prefer_const_literals_to_create_immutables
    - prefer_contains
    - prefer_equal_for_default_values
    - prefer_final_fields
    - prefer_final_locals
    - prefer_foreach
    - prefer_initializing_formals
    - prefer_is_empty
    - prefer_is_not_empty
    - prefer_iterable_whereType
    - prefer_single_quotes
    - prefer_void_to_null
    - recursive_getters
    - file_names
    - library_names
    - library_prefixes
    - lines_longer_than_80_chars
    - list_remove_unrelated_type
    - no_duplicate_case_values
    - non_constant_identifier_names
    - prefer_asserts_in_initializer_lists
    - prefer_collection_literals
    - prefer_conditional_assignment
```