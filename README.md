# n8n-MCP
An AI support agent that uses three tools exposed through an MCP server, made entirely in n8n
https://drive.google.com/file/d/1i1j6VjV0iZTbMAgXBLW0ZwtQOUTAFJtk/view?usp=sharing
Working proof of the support agent made, shown through the video.

So, this support agent is a n8n-based workflow, which uses three tools- Send customer email, notify ops and create ticket, hosted through a mcp server.
Each of these carry a different function of 

Send-customer-email - Takes in input in three fields, "to", "subject" and "body", normalizes it to lowercase and the if node makes sure that the input matches, and if it does it sends the mail to the customer regarding that his request has been seen and the team is working out solutions for it, IF node fails -> otherwise gives out a message invalid_input.

Create-ticket - Take in input in four fields, "order_id", "category", "summary" and "priority" -> normalizes -> If -> and fills this data in a data table, if fails then gives out a message invalid_input (same as before).

notify-ops - Takes in input in three fields, "severity", "message", "order_id" -> normalizes -> If true sends an email notifying the team about what needs immediate attention, If Node fails -> gives out a mesasge invalid_input.

The MCP head was configured for each using the from ai settings and for each of the tool and for each of the field in the tool a bried description was passed, so that the AI can fill that in from the query written in the chat.
So as u can see in the video that the query was written "Order 330 is 5 days late and my email is customer@example.com" 
From that the AI model (Gemini-3.1 Flash) used all of the three tools
For send customer email it sent that "We have received your report regarding order 330 being late. A high-priority support ticket has been created, and our operations team has been notified to investigate the delay." It also created a ticket as shown in the video and also sent another email but this one to the team regarding that this product is of high priority as it is 5 days late.


**The stack used to make this was just n8n and Mailpit for emails testing. Both were locally hosted.
It is a quite simple but effective project that has helped me understand how MCP works.
I have tried various tests on this workflows and they all came as they should such as the AI pointing out if the data is wrong and not calling any tools.**
**What i hope to take away from this project and improve**
Concept of MCP and integrating it in my other workflows with proper authentication. (This one did lack authentication for the AI, but according to the tools that it is given i think that's okay)
The only documentation that i read to understand the logic behind the concept was this https://modelcontextprotocol.io/docs/2026-07-28/getting-started/intro and from this i also read about streamable http and authentication.




