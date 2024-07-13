# Data normalisation in Microsoft Sentinel

#### Intro

As we know MS Sentinel ingests from many different sources to to make it easier for you to understand the information in one common langauge is a big challenge for any kind of data analyst.



#### Main ASIM (Advanced Security Information Model) components

* Normalized schemas
* Parsers
* Content for each normalized schema

To view your parsers, they are located here:

* Navigate to your Microsoft Sentinel workspace in the Azure portal
* Select Logs from the left navigation
* Expand the schema and filter pane on the left side (if needed use the ellipsis to reveal all the tools)
* Select Functions
* Expand Microsoft Sentinel

#### Deploy parsers <a href="#deploy-parsers" id="deploy-parsers"></a>

Deploy parsers manually by copying them to the Azure Monitor Log page and saving the query as a function. This method is useful for testing. For more information, see Create a function.

To deploy a large number of parsers, we recommend using parser ARM templates, as follows:

1. Create a YAML file based on the relevant template for each schema and include your query in it. Start with the YAML template relevant for your schema and parser type, filtering or parameter-less.
2. Use the ASIM Yaml to ARM template converter to convert your YAML file to an ARM template.
3. If deploying an update, delete older versions of the functions using the portal or the function delete PowerShell tool.
4. Deploy your template using the Azure portal or PowerShell.

You can also combine multiple templates to a single deploy process using linked templates.



Source is the name of the virtual table.

starttime and endtime parameters are the supported filtering parameters.
