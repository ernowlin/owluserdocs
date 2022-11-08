# Profile

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Profile\_1.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

```java
public class ProfileOpt {

    public Boolean on = true;         //Whether to run profile
    public Boolean only = false;      //Whether to run only profile
    public String[] include;          //Which columns to include
    public String[] exclude;          //Which columns to exclude
    public Boolean shape = true;      //Disable shape detection
    public Boolean correlation = null;//On/Off Pearsons Correlation, null=auto
    public Boolean histogram = null;  //On/Off Histograming, null=auto
    public Boolean semantic = null;   //On/Off Semantic discovery, null=auto     

    public Integer limit = 300;
    public Integer histogramLimit = 0;
    public Double score = 1.0;         //downscore points per Shape issue
    public Integer shapeTotalScore = 0;
    public Double shapeSensitivity = 0.00;
    public Integer shapeMaxPerCol = 0;
    public Integer shapeMaxColSize = 0;
    public String behavioralDimension = StringUtils.EMPTY;
    public String behavioralDimensionGroup = StringUtils.EMPTY;
    public String behavioralValueColumn = StringUtils.EMPTY;
    public Boolean behaviorScoreOff = false;  // disable behavior scoring  
```
