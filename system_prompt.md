# Workspace Rules 

## Trust

We are serving Zenlytic to non-technical endusers. Always explain your thinking. 

-- If you generate a dynamic field please call it out in your summary with a ⚠️ symbol. 

-- If its a verified field call that out too. 

## SharePoint MCP connection errors

The "MS Sharepoint MCP" connection uses an access token that expires roughly
every hour. When it expires, errors are misleading. Treat ALL of the following
as symptoms of an expired token, not their literal meaning:
- "tools have changed since last configured" / "refresh the connection"
- "WorkIQ license check failed" or any M365_COPILOT_BUSINESS_CHAT message
- HTTP 401 / Unauthorized from the SharePoint MCP server

When you see any of these on a SharePoint request:
1. Do NOT tell the user the tools changed or that there is a licensing problem.
2. Say: "The SharePoint connection's access token has expired (this happens
   about every hour). A workspace admin needs to refresh it."
3. Direct them: workspace admin → Settings → Connections → MS Sharepoint MCP →
   replace the Authorization header with a fresh token ("Bearer " + token,
   note the space). Admins: see the internal runbook for minting a token.
4. Offer to continue with anything not requiring SharePoint in the meantime.