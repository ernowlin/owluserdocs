# Source

{% hint style="info" %}
We've moved! To improve customer experience, the Collibra Data Quality User Guide has moved to the [Collibra Documentation Center](https://productresources.collibra.com/docs/collibra/latest/Content/DataQuality/DQApis/Source.htm) as part of the Collibra Data Quality 2022.11 release. To ensure a seamless transition, [dq-docs.collibra.com](http://dq-docs.collibra.com/) will remain accessible, but the DQ User Guide is now maintained exclusively in the Documentation Center.
{% endhint %}

```java
public class SourceOpt {

    public Boolean on = false;              //-vs
    public Boolean only = false;            //-sourceonly
    public Boolean validateValues = false;  //-validatevalues
    public Boolean matches = false;         //-matches

    public String[] include;               //-valinc
    public String[] exclude;               //-valexc
    public String[] key;                    //valkey
    public Map<String, String> map;         //
    public Double score = 1.0;              // points per validate source found, default 1-5
    public Integer limit = 30;              //-valsrclimit
    public String delimiter = ",";          //-srcdel
    public String fileCharSet = "UTF-8";     //-srcencoding
    public String filePath = StringUtils.EMPTY; //--srcfile

    public String header = null;            //-srcheader
    public String dataset = StringUtils.EMPTY;
    public String driverName = StringUtils.EMPTY;
    public String user = StringUtils.EMPTY;
    public String password = StringUtils.EMPTY;
    public String passwordManager = StringUtils.EMPTY;
    public String connectionName = StringUtils.EMPTY;
    public String connectionUrl = StringUtils.EMPTY;
    public String query = StringUtils.EMPTY;
    public String fileQuery = StringUtils.EMPTY;
    public String lib = StringUtils.EMPTY;
    public Properties connectionProperties;
```
