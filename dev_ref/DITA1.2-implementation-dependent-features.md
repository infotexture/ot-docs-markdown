# Implementation dependent features

## Chunking

Supported chunking methods:

-   select-topic
-   select-document
-   select-branch
-   by-topic
-   by-document
-   to-content
-   to-navigation.

When no chunk attribute values are given, no chunking is performed.

**Note:** In effect, for HTML based transformation types this is equivalent to select-document and by-document defaults.

Error recovery:

-   When two tokens from the same category are used, no error or warning is thrown.
-   When an unrecognized chunking method is used, no error or warning is thrown.

## Filtering

Error recovery:

-   When there are multiple `revprop` elements with the same val attribute, no error or warning is thrown
-   When multiple prop elements define a duplicate attribute and value combination, attribute default, or fall-back behaviour, DOTJ007E error is thrown.

## Debug attributes

The debug attributes are populated as follows:

 xtrf
 :   absolute system path of the source document

  xtrc
 :   element counter that uses the format

    ```
    element-name ":" integer-counter ";" line-number ":" column-number
    ```

 ## Image scaling

If both height and width attributes are given, image is scaled non-uniformly.

If scale attribute is not an unsigned integer, no error or warning is thrown during preprocessing.

## Map processing

When a `topicref` element that references a map contains child `topicref` elements, DOTX068W error is thrown and the child `topicref` elements are ignored.

## Link processing

When the value of `href` attribute is not a valid URI reference, DOTJ054E error is thrown. Depending on [error recover mode](../parameters/parameters-base.md#processing-mode), error recover may be attempted.

## Copy-to processing

When the `copy-to` attribute is specified on a `topicref`, the content of the `shortdesc` element is not used to override the short description of the topic.

