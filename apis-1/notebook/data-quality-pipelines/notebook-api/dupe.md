# Dupe

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Dupe.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

```java
package com.owl.common.options;

/**
 * Options for Dupe Activity
 */
public class DupeOpt {

    /**
     * Whether to run Dupe Activity
     */
    public Boolean on = false;          // --dupe

    /**
     * @deprecated Unused for Activity2
     */
    public Boolean only = false;        // --dupeonly

    /**
     * Column names to include Dupe Activity
     */
    public String[] include;            // -dupeinc

    /**
     * Column names to exclude Dupe Activity
     */
    public String[] exclude;            // dupeexc

    /**
     * Indicator for complexity. See Activity2.Dupe.Scala.execute()
     * depth == 0 : exact match (sets props.dupeExactMatch = TRUE downstream)
     */
    public Integer depth = 2;           // -depth

    /**
     * The minimum dupe scores between two duplicates. (currently calculated as "edit distance", out of upperBound)
     * Two values with dupe score less than this is lowerBound are not duplicates (i.e. "truly" different values)
     */
    public Integer lowerBound = 80;     // -dupelb, -dupecutoff

    /**
     * The maximum possible dupe score for duplicate records (for a given dupe detection method).
     * Currently assumed to be 100.
     */
    public Integer upperBound = 100;    // -dupeub, -dupepermatchupperlimit

    /**
     * Approximate dupe score used to create block index (when DF is large)
     */
    public Integer approximate = 1;     // -dupeapprox

    /**
     * Number of observations per unique duplicate
     */
    public Integer limitPerDupe = 15;

    /**
     * Whether to process column headers when data load uses manual column names (LoadOpts.fileHeader)
     * TODO this belongs in LoadOpts, not DupeOpts
     */
    public Boolean checkHeader = true;

    /**
     * TODO remove
     *
     * @deprecated not used;
     */
    public String filter;

    /**
     * If true, dupe activity is case insensitive. If false, dupe activity is case sensitive.
     * Convenience feature for upper and lower set to 100
     */
    public Boolean ignoreCase = false;      //-dupenocase

    /**
     * Number of points each duplicate contributes to the total schema score (in Hoot)
     */
    public Double score = 1.0;               //-dupescore  points per duplicate found default 1

    /**
     * Number of unique duplicates to compute during dupe activity
     */
    public Integer limit = 300;               //-dupelimit  default 300
```
