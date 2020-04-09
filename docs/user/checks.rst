Checks and fixups
=================

The quality checks help catch common translator errors, ensuring the
translation is in good shape. The checks are divided into three levels of severity,
and can be ignored in case of false positives.

Once submitting a translation with a failing check, this is immediately shown to
the user:

.. image:: /images/checks.png


.. _autofix:

Automatic fixups
----------------

In addition to :ref:`checks`, Weblate can also fix some common
errors in translated strings automatically. Use it with caution to not have
it add errors.

.. seealso::

   :setting:`AUTOFIX_LIST`

.. _checks:

Quality checks
--------------

Anuvad employs a wide range of quality checks on strings. The following section
describes them all in further detail. There are also language specific checks.
Please file a bug if anything is reported in error.

.. seealso::

   :setting:`CHECK_LIST`, :ref:`custom-checks`

Translation checks
------------------

Executed upon every translation change, helping translators maintain
good quality translations.

.. _check-same:

Unchanged translation
~~~~~~~~~~~~~~~~~~~~~

Happens if the source and corresponding translation strings is identical, down to
at least one of the plural forms. Some strings commonly found across all
languages are ignored, and various markup is stripped. This reduces
the number of false positives.

This check can help find strings mistakenly untranslated.

The default behavior of this check is to exclude words from the built-in
blacklist from the checking. These are words which are frequently not being
translated. This is useful to avoid false positives on short strings, which
consist only of single word which is same in several languages. This blacklist
can be disabled by adding ``strict-same`` flag to string or component.

.. seealso::

   :ref:`component`,
   :ref:`custom-checks`

.. _check-begin-newline:
.. _check-end-newline:

Starting or trailing newline
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Source and translation do not both start (or end) with a newline.

Newlines usually appear in source strings for good reason, omissions or additions
can lead to formatting problems when the translated text is put to use.

.. _check-begin-space:

Starting spaces
~~~~~~~~~~~~~~~

Source and translation do not both start with the same number of spaces.

A space in the beginning of a string is usually used for indentation in the interface and thus
important to keep.

.. _check-end-space:

Trailing space
~~~~~~~~~~~~~~

Checks that trailing spaces are replicated between both source and translation.

Trailing space is usually utilized to space out neighbouring elements, so
removing it might break layout.

.. _check-double-space:

Double space
~~~~~~~~~~~~~~

Checks that double space is present in translation to avoid false positives on other space-related checks.

Check is false when double space is found in source meaning double space is intentional.

.. _check-end-stop:

Trailing stop
~~~~~~~~~~~~~

Checks that full stops are replicated between both source and translation.
The presence of full stops is checked for various languages where they do not belong
(Chinese, Japanese, Devanagari or Urdu).

.. seealso::

   `Full stop on Wikipedia <https://en.wikipedia.org/wiki/Full_stop>`_

.. _check-end-colon:

Trailing colon
~~~~~~~~~~~~~~

Checks that colons are replicated between both source and translation. The
presence of colons is also checked for various languages where they do not
belong (Chinese or Japanese).

.. seealso::

   `Colon on Wikipedia <https://en.wikipedia.org/wiki/Colon_(punctuation)>`_

.. _check-end-question:

Trailing question mark
~~~~~~~~~~~~~~~~~~~~~~

Checks that question marks are replicated between both source and translation.
The presence of question marks is also checked for various languages where they
do not belong (Armenian, Arabic, Chinese, Korean, Japanese, Ethiopic, Vai or
Coptic).

.. seealso::

   `Question mark on Wikipedia <https://en.wikipedia.org/wiki/Question_mark>`_

.. _check-end-exclamation:

Trailing exclamation
~~~~~~~~~~~~~~~~~~~~

Checks that exclamations are replicated between both source and translation.
The presence of exclamation marks is also checked for various languages where
they do not belong (Chinese, Japanese, Korean, Armenian, Limbu, Myanmar or
Nko).

.. seealso::

   `Exclamation mark on Wikipedia <https://en.wikipedia.org/wiki/Exclamation_mark>`_

.. _check-punctuation-spacing:

Punctuation spacing
~~~~~~~~~~~~~~~~~~~

.. versionadded:: 3.9

Checks that there is non breakable space before double punctuation sign
(exclamation mark, question mark, semicolon and colon). This rule is used only
in a few selected languages like French or Breton, where space before double
punctuation sign is a typographic rule.

.. seealso::

   `French and English spacing on Wikipedia <https://en.wikipedia.org/wiki/History_of_sentence_spacing#French_and_English_spacing>`_

.. _check-end-ellipsis:

Trailing ellipsis
~~~~~~~~~~~~~~~~~

Checks that trailing ellipses are replicated between both source and translation.
This only checks for real ellipsis (``…``) not for three dots (``...``).

An ellipsis is usually rendered nicer than three dots in print, and sounds better with text-to-speech.

.. seealso::

   `Ellipsis on Wikipedia <https://en.wikipedia.org/wiki/Ellipsis>`_


.. _check-end-semicolon:

Trailing semicolon
~~~~~~~~~~~~~~~~~~

Checks that semicolons at the end of sentences are replicated between both source and translation.
This can be useful to keep formatting of entries such as desktop files.

.. seealso::

   `Semicolon on Wikipedia <https://en.wikipedia.org/wiki/Semicolon>`_

.. _check-max-length:

Maximum length
~~~~~~~~~~~~~~

Checks that translations are of acceptable length to fit available space.
This only checks for the length of translation characters.

Unlike the other checks, the flag should be set as a ``key:value`` pair like
``max-length:100``.

.. _check-python-format:
.. _check-python-brace-format:
.. _check-php-format:
.. _check-c-format:
.. _check-perl-format:
.. _check-javascript-format:
.. _check-angularjs-format:
.. _check-c-sharp-format:
.. _check-java-format:
.. _check-java-messageformat:
.. _check-qt-format:
.. _check-qt-plural-format:
.. _check-ruby-format:
.. _check-i18next-interpolation:

Inconsistent
~~~~~~~~~~~~

Anuvad checks translations of the same string across all translation within a
project to help you keep consistent translations.

The check fails on differing translations of one string within a project. This can also lead to
inconsistencies in displayed checks. You can find other translations of this
string on the :guilabel:`Other occurences` tab.

.. seealso::

   :ref:`translation-consistency`

.. _check-translated:

Has been translated
~~~~~~~~~~~~~~~~~~~

Means a sentence has been translated already. This can happen when the
translations have been reverted in VCS or lost otherwise.

.. _check-escaped-newline:

Mismatched \\n
~~~~~~~~~~~~~~

Usually escaped newlines are important for formatting program output.
Check fails if the number of ``\\n`` literals in translation do not match the source.

.. _check-newline:

Mismatched \n
~~~~~~~~~~~~~~

Usually newlines are important for formatting program output.
Check fails if the number of ``\n`` literals in translation do not match the source.

.. _check-bbcode:

BBcode markup
~~~~~~~~~~~~~

BBCode represents simple markup, like for example highlighting important parts of a
message in bold font, or italics.

This check ensures they are also found in translation.

.. note::

    The method for detecting BBcode is currently quite simple so this check
    might produce false positives.

.. _check-zero-width-space:

Zero-width space
~~~~~~~~~~~~~~~~

Zero-width space (<U+200B>) characters are used to break messages within words (word wrapping).

As they are usually inserted by mistake, this check is triggered once they are present
in translation. Some programs might have problems when this character is used.

.. seealso::

    `Zero width space on Wikipedia <https://en.wikipedia.org/wiki/Zero-width_space>`_


.. _check-xml-invalid:

Maximum size of translation
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. versionadded:: 3.7

Translation rendered text should not exceed given size. It renders the text
with line wrapping and checks if it fits into given boundaries.

This check needs one or two parameters - maximal width and maximal number of
lines. In case the number of lines is not provided, one line text is
considered.

You can also configure used font by ``font-*`` directives (see
:ref:`custom-checks`), for example following translation flags say that the
text rendered with ubuntu font size 22 should fit into two lines and 500
pixels:

.. code-block:: text

   max-size:500:2, font-family:ubuntu, font-size:22

.. hint::

   You might want to set ``font-*`` directives in :ref:`component` to have the same
   font configured for all strings within a component. You can override those
   values per string in case you need to customize it per string.

.. seealso::

   :ref:`fonts`, :ref:`custom-checks`

Source checks
-------------

Source checks can help contributors improve the quality of source sentences.

.. _check-optional-plural:

Multiple failing checks
~~~~~~~~~~~~~~~~~~~~~~~

Numerous translations of this string have failing quality checks. This is
usually an indication that something could be done to improve the source
string.

This check failing can quite often be caused by a missing full stop at the end of
a sentence, or similar minor issues which translators tend to fix in
translation, while it would be better to fix it in the source string.
