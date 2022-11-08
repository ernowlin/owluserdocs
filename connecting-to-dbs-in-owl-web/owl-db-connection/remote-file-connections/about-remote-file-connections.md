# About remote file connections

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DBConnection/about-remote-file-connections.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

This section is an overview of the supported data file formats and the limitations of connecting to a remote file.&#x20;

## Supported file types

File formats differ in structure, so you might need to prepare your data before establishing a connection.&#x20;

| Type                       | File structure  | Notes                                              |
| -------------------------- | --------------- | -------------------------------------------------- |
| Delimited (CSV, TSV, etc.) | Structured      | The default delimiter is comma (for example, CSV). |
| Parquet                    | Structured      |                                                    |
| Avro                       | Structured      |                                                    |
| JSON                       | Semi-structured |                                                    |
| ORC                        | Semi-structured |                                                    |
| XML                        | Semi-structured |                                                    |
| Delta                      | Semi-structured |                                                    |

## Supported delimiters

The following table is a list of supported delimiters available in the Delimiter dropdown menu.

| Type         | Format | Description                                                                                                     |
| ------------ | ------ | --------------------------------------------------------------------------------------------------------------- |
| Comma        | CSV    | <p><code>,</code> is used to separate values in the file. <br><br>This is the default delimiter for files. </p> |
| Tab          | TSV    | `tab` is used to separate values in the file.                                                                   |
| Semicolon    | CSV    |  `;` is used to separate values in the file.                                                                    |
| Double Quote | CSV    | `"` is used to separate values in the file.                                                                     |
| Single Quote | CSV    | `'` is used to separate values in the file.                                                                     |
| Pipe         | TXT    | `\|` is used to separate values in the text file.                                                               |
| SOH          | TXT    | A Unicode character 'START OF HEADING' (U+0001) is an invisible control character.                              |
| Custom       | N/A    | Add a custom delimiter. Support for custom delimiters may vary.                                                 |
