Translating using Anuvad
=========================

Thank you for interest in translating using Anuvad. COVID19 topics can either be
set up for direct translation, or by way of accepting suggestions made by
users without accounts.

Overall, there are two modes of translation:

* The COVID19 topic accepts direct translations
* The COVID19 topic accepts only suggestions, which are automatically validated once a defined number of votes is reached

Please see :ref:`workflows` for more information on translation workflow.

Options for translation project visibility:

* Publicly visible and anybody can contribute
* Visible only to a certain group of translators

.. seealso::

   :ref:`privileges`,
   :ref:`workflows`

Translation projects
--------------------

Translation projects hold related resources, related to the same topic.

.. image:: /images/project-overview.png

.. _strings-to-check:

Translation links
-----------------

Having navigated to a resource, a set of links lead to actual translation.
The translation is further divided into individual checks, like
:guilabel:`Untranslated` or :guilabel:`Needing review`.  If the whole project
is translated, without error, :guilabel:`All translations` is still available.
Alternatively you can use the search field to find a specific string or term.

.. image:: /images/strings-to-check.png

Suggestions
-----------

.. note::

    Actual permissions might vary depending on your Anuvad configuration.

Anonymous users can only (if permitted) forward suggestions.  Doing so is still
available to signed in users, in cases where uncertainty about the translation
arises, which will prompt another translator to review it.

The suggestions are scanned on a daily basis to remove duplicate ones or
suggestions that match the current translation.

Comments
--------

The comments can be posted in two scopes - source sentence or translation. Choose
the one which matches the topic you want to discuss. The source sentence comments are
good for prividing feedback on the original string, for example that it should
be rephrased or it is confusing.

You can use Markdown syntax in the comments and mention other users using
``@mention``.

Shapings
--------

Shapings are used to group variants of the string in different lengths. The
frontend can use different strings depending on the screen or window size.

.. seealso::

    :ref:`shapings`

Labels
------

Labels are used to categorize strings within a topic. These can be used to
further customize the localization workflow, for example to define categories
of strings.

.. seealso::

    :ref:`labels`

Translating
-----------

On the translation page, the source string and an edit area for translating are shown.
Should the translation be plural, multiple source strings and edit areas are
shown, each described and labeled in plural form.

All special whitespace characters are underlined in red and indicated with grey
symbols. More than one subsequent space is also underlined in red to alert the translator to
a potential formatting issue.

Various bits of extra information can be shown on this page, most of which coming from the project source code
(like context, comments or where the message is being used). When you choose secondary languages in your
preferences, translation to these languages will be shown (see :ref:`secondary-languages`) above the source string.

Below the translation, any suggestion made by others will be shown, which you
can in turn accept, accept with changes, or delete.

Keyboard shortcuts
++++++++++++++++++

The following keyboard shortcuts can be utilized during translation:

:kbd:`Alt+Home`
    Navigates to first translation in current search.
:kbd:`Alt+End`
    Navigates to last translation in current search.
:kbd:`Alt+PageUp`
    Navigates to previous translation in current search.
:kbd:`Alt+PageDown`
    Navigates to next translation in current search.
:kbd:`Ctrl+Enter` or :kbd:`Option+Enter`
    Saves current translation.
:kbd:`Ctrl+Shift+Enter` or :kbd:`Option+Shift+Enter`
    Unmarks translation as fuzzy and submits it.
:kbd:`Ctrl+E` or :kbd:`Option+E`
    Focus translation editor.
:kbd:`Ctrl+U` or :kbd:`Option+U`
    Focus comment editor.
:kbd:`Ctrl+M` or :kbd:`Option+M`
    Shows machine translation tab.
:kbd:`Ctrl+<NUMBER>` or :kbd:`Option+<NUMBER>`
    Copies placeable of given number from source string.
:kbd:`Ctrl+M <NUMBER>` or :kbd:`Option+M <NUMBER>`
    Copy machine translation of given number to current translation.
:kbd:`Ctrl+I <NUMBER>` or :kbd:`Option+I <NUMBER>`
    Ignore failing check of given number.
:kbd:`Ctrl+J` or :kbd:`Option+J`
    Shows nearby strings tab.
:kbd:`Ctrl+S` or :kbd:`Option+S`
    Shows search tab.
:kbd:`Ctrl+O` or :kbd:`Option+O`
    Copies source string.
:kbd:`Ctrl+T` or :kbd:`Option+T`
    Toggles "Needs editing" flag.


.. _source-context:

Translation context
+++++++++++++++++++

This contextual description provides related information about the current string.

String attributes
    Things like message ID, context (``msgctxt``) or location in source code.
Screenshots
    Screenshots can be uploaded to Weblate to better inform translators
    of where and how the string is used, see :ref:`screenshots`.
Nearby strings
    Displays neighbouring messages from the translation file. These
    are usually also used in a similar context and prove useful in keeping the translation consistent.
Other occurences
    In case a message appears in multiple places (e.g. multiple resources),
    this tab shows all of them if they are found to be inconsistent (see
    :ref:`check-inconsistent`). You can choose which one to use.
Translation memory
    Look at similar strings translated in past, see :ref:`memory`.
Glossary
    Displays terms from the project glossary used in the current message.
Recent edits
    List of people whom have changed this message recently using Weblate.
Topic
    Topic information like instructions for translators, or information about
    its version control system repository.

If the translation format supports it, you can also follow supplied links to respective
source code containing each source string.

Translation history
+++++++++++++++++++

Every change is by default (unless turned off in resource settings) saved in
the database, and can be reverted. Optionally one can still also revert anything
in the underlying version control system.

Translated string length
++++++++++++++++++++++++

Anuvad can limit length of translation in several ways to ensure the
translated string is not too long:

* The default limitation for translation is ten times longer than source
  string. This can be turned of by
  :setting:`LIMIT_TRANSLATION_LENGTH_BY_SOURCE_LENGTH`. In case you are hitting
  this, it might be also caused by monolingual translation being configured as
  bilingual, making Weblate see translation key as source string instead of the
  actual source string. See :ref:`bimono` for more info.
* Maximal length in characters defined by translation file or flag, see
  :ref:`check-max-length`.
* Maximal rendered size in pixels defined by flags, see :ref:`check-max-size`.

Glossary
--------

Each project can have an assigned glossary for any language as a shorthand for storing terminology.
Consistency is more easily maintained this way.
Terms from the currently translated string can be displayed in the bottom tabs.

Managing glossaries
+++++++++++++++++++

On the :guilabel:`Glossaries` tab of each project page, you can edit
existing glossaries. An empty glossary for a given project is automatically created when a language is added to a component (to do this, select a component, its :guilabel:`Translation` tab and click :guilabel:`Add new language for translation`). Once a glossary exists, it will also show up in this list.

.. image:: /images/project-glossaries.png

Glossaries are shared among all components of the same project.

On this list, you can choose which glossary to manage (all languages used in
the current project are shown). Following one of the language links will lead you to a page
which can be used to edit, import or export the selected glossary, or view the edit history:

.. image:: /images/glossary-edit.png

.. _machine-translation:

Machine translation
-------------------

Based on configuration and your translated language, Anuvad provides you
suggestions from several machine translation tools. All machine translations
are available in a single tab of each translation page.

.. seealso::

   You can find the list of supported tools in :ref:`machine-translation-setup`.

.. _auto-translation:

Automatic translation
---------------------

You can use automatic translation to bootstrap translation based on external sources.
This tool is called :guilabel:`Automatic translation` accessible in the :guilabel:`Tools` menu, once you have selected a component and a language:

.. image:: /images/automatic-translation.png

Two modes of operation are possible:

- Using other Weblate components as a source for translations.
- Using selected machine translation services with translations above a certain
  quality threshold.

You can also choose which strings are to be auto-translated.

.. warning::

    Be mindful that this will overwrite existing translations if employed with
    wide filters such as :guilabel:`All strings`.

Useful in several situations like consolidating translation
between different components (for example website and application) or when
bootstrapping translation for a new component using existing translations
(translation memory).

.. seealso::

    :ref:`translation-consistency`

.. _user-rate:

Rate limiting
-------------

To avoid abuse of the interface, there is rate limiting applied to several
operations like searching, sending contact form or translating. In case you are
are hit by this, you are blocked for a certain period until you can perform the
operation again.

The default limits are described in the administrative manual in
:ref:`rate-limit`, but can be tweaked by configuration.
