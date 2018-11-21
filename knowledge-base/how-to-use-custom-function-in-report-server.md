---
title: How to configure Telerik Report Server to use reports with custom functions
description: How to configure Telerik Report Server to use reports with custom functions
type: how-to
page_title: How to configure Telerik Report Server to use reports with custom functions
slug: how-to-use-custom-function-in-report-server
position: 
tags: programming,functions,aggregates
ticketid: 1148325
res_type: kb
---

## Environment
<table>
	<tr>
		<td>Product</td>
		<td>Progress® Telerik® Report Server</td>
	</tr>
</table>


## Description
Extending the report engine of the Report Server is not supported out of the box. It requires some manual steps.

## Solution

<ol>
	<li>Copy the assembly containing the user function(s) in:
		<ul>
			<li>
				The bin folder of the Report Server web application, i.e. [Telerik Report Server installation folder]\Telerik.ReportServer.Web\bin (usually <b>C:\Program Files (x86)\Progress\Telerik Report Server\Telerik.ReportServer.Web\bin</b>)
			</li>
			<li>
				for scheduling services only - in the folder of the scheduling service, i.e. [Telerik Report Server installation folder]\Services (usually <b>C:\Program Files (x86)\Progress\Telerik Report Server\Services</b>)
			</li>
		</ul>
	</li>
	<li>Register the same assembly in the corresponding application configuration files, using the snippets that could be found <a href="https://docs.telerik.com/reporting/standalone-report-designer-extending-configuration">here</a>.
		<ul>
			<li>
				in [Telerik Report Server installation folder]\Telerik.ReportServer.Web\Web.config (usually <b>C:\Program Files (x86)\Progress\Telerik Report Server\Telerik.ReportServer.Web\Web.config</b>)
			</li>
			<li>
				for scheduling services only in [Telerik Report Server installation folder]\Services\Telerik.ReportServer.ServiceAgent.exe.config (usually <b>C:\Program Files (x86)\Progress\Telerik Report Server\Services\Telerik.ReportServer.ServiceAgent.exe.config</b>)
			</li>
		</ul>
	</li>
</ol>

If the custom functions are aggregate functions, it would be necessary the Telerik Reporting version used for creating the custom assembly, and the one used in Telerik Report Server to match. If the Telerik Reporting version on the Report Server is newer, you could use binding redirect to point the version of Telerik Reporting used to create the aggregate function in the same way as explained in [this help article](https://docs.telerik.com/reporting/standalone-report-designer-configuration/).
