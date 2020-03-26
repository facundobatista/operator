# The Operator Framework

The Operator Framework provides a simple, lightweight, and powerful way of
encapsulating operational experience in code.

The framework will help you to:

* model the integration of your services
* manage the lifecycle of your application
* create reusable and scalable components
* keep your code simple and readable

## Getting Started

Charms written using the operator framework are just python code. The intention
is for it to feel very natural for somebody used to coding in python, and
reasonably easy to pick up for somebody whose expertise is domain-specific and
not necessarily a pythonista themselves. The dependencies of the operator
framework itself are kept as minimal as possible; currently that's just `PyYAML`
(which is included in Ubuntu's cloud images by default), and optionally `rpdb`
if you want to be able to use the live debugger.

If you're new to the world of juju and charms, you should probably dive into the
[tutorial](/TBD).

If you know about juju, and have written charms that didn't use the operator
framework (be it with reactive or without), we have an [introduction to the
operator framework](/TBD) just for you.

## Testing your charms

The operator framework provides a testing harness, so that you can test that
your charm does the right thing when presented with different scenarios, without
having to have a full deployment to do so. `pydoc3 ops.testing` has the details
for that, including this example:

```python
harness = Harness(MyCharm)
# Do initial setup here
relation_id = harness.add_relation('db', 'postgresql')
# Now instantiate the charm to see events as the model changes
harness.begin()
harness.add_relation_unit(relation_id, 'postgresql/0', remote_unit_data={'key': 'val'})
# Check that charm has properly handled the relation_joined event for postgresql/0
self.assertEqual(harness.charm. ...)
```

# Talk to us

If you need help, have ideas, or would just like to chat with us, reach out on
IRC: we're in [#smooth-operator](irc://chat.freenode.net/%23smooth-operator) on
freenode (or try the [webchat](https://webchat.freenode.net/#smooth-operator)).

We also pay attention to juju's [discourse](https://discourse.jujucharms.com/),
but currently we don't actively post there; most discussion at this stage is on
IRC.

# Operator Framework development

If you want to work in the framework *itself* you will need the following
depenencies installed in your system:

- Python >= 3.5
- PyYAML
- autopep8
- flake8

Then you can try `./run_tests`, it should all go green.
