---
title: "&lt;workflowInstanceQueries&gt; of WCF"
ms.date: "03/30/2017"
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
---
# &lt;workflowInstanceQueries&gt; of WCF

Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.  
  
For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<tracking>  
\<profiles>  
\<trackingProfile>  
\<workflow>  
\<workflowInstanceQueries>  
  
## Syntax  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name"/>
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```
  
## Attributes and elements

The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  

None.  
  
### Child elements  
  
|Element|Description|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery-of-wcf.md)|A query that is used to track workflow instance life cycle changes.|  
  
### Parent elements  
  
|Element|Description|  
|-------------|-----------------|  
|[\<workflow>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.|  
  
## Remarks

The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## Example  

The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>  
    <states>  
      <state name="Started"/>  
    </states>  
  </workflowInstanceQuery>  
</workflowInstanceQueries>
```
  
## See also

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
