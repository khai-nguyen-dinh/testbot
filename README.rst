PyAIML for Python 3 -- The Python AIML Interpreter
==================================================

Author: Cort Stratton (cort@users.sourceforge.net)

Web: http://pyaiml.sourceforge.net/

Python 3 version: https://github.com/warvariuc/pyaiml

PyAIML is an interpreter for AIML (the Artificial Intelligence Markup Language), implemented
entirely in standard Python.  It strives for simple, austere, 100% compliance with the AIML 1.0.1
standard, no less and no more.

This is currently pre-alpha software.  Use at your own risk!

For information on what's new in this version, see the ``CHANGES.rst`` file.

For information on the state of development, including the current level of ``AIML 1.0.1``
compliance, see the ``SUPPORTED_TAGS.txt`` file.

Quick & dirty example (assuming you've downloaded the "standard" AIML set):

.. code-block:: python
    
    import aiml

    # The Kernel object is the public interface to the AIML interpreter.
    k = aiml.Kernel()

    # Use the 'learn' method to load the contents of an AIML file into the Kernel.
    k.learn("sets/std-startup.xml")

    # Use the 'respond' method to compute the response to a user's input string.
    # respond() returns the interpreter's response, which in this case we ignore.
    k.respond("load aiml b")

    # Loop forever, reading user input from the command line and printing responses.
    while True: print k.respond(input("> "))


TODO
----

Laundry list of future tasks, in no particular order:

- AIML 1.0.1 compliance (highest priority):

  - Unknown yet well-defined elements (e.g. HTML) inside templates (see sections 3.2, 3.6).
  - ``AimlParser._validate_elem_start()`` needs to test the well-formedness of attribute values
    (for example, making sure that the "index" attribute has an integer value, and not a string).
    UPDATE: this works for ``<star>``, ``<thatstar>`` and ``<topicstar>``.  Still needs to be
    written for ``<input>`` and ``<that>``, which take either an integer or an integer pair.

- Support the Program D startup file syntax, or something similar?  It seems to be a good way to
  initialize bot settings and substitutions.
- Documentation/tutorials.
