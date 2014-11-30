Works like normal inclusion tag but it allows the wrapped function to specify which template to use, or to abort althogether and return.

Here is an example.

Define a django template tag, and wrap it with this decorator like below:

    @configurable_inclusion_tag(register)
    def maybe_show_foo(context):
        if not SHOULD_SHOW_FOO:
            return None
        return 'foo.html', context

In a template, call the template tag(example: `{% maybe_show_foo %}` ).
