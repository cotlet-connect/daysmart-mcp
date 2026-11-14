# DaySmart MCP server

Connect DaySmart Salon or DaySmart Pet to ChatGPT, Claude and any AI agent through Cotlet.dev. The hosted connector exposes 15 DaySmart tools over MCP and REST while you keep your own DaySmart login.

DaySmart Salon and DaySmart Pet do not provide a public API or MCP server. Cotlet works in the signed-in DaySmart cloud and is independent from DaySmart.

## What you can automate

- Read the appointment book and employees
- Book, update or void appointments after your approval
- Find clients, pets and waitlist entries
- Keep pet notes and vaccination dates current
- Send Ready For Pickup texts after your approval
- Read sales and other reports

## Connect in 2 minutes

Create an account at https://cotlet.dev, sign in to DaySmart in your Cotlet Cloud Browser and enable DaySmart for agents. Add this MCP address to your client:

```
https://cotlet.dev/mcp/v1/connect
```

Claude Code:

```bash
claude mcp add --transport http cotlet-daysmart https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

ChatGPT and other OAuth clients can use the connector address above. API clients store a Cotlet API key as `COTLET_API_KEY`.

## Run the local stdio bridge

This repository contains a small stdlib-only MCP bridge. It lists DaySmart helper tools locally and forwards calls to the hosted Cotlet server.

```bash
pip install daysmart-mcp
export COTLET_API_KEY="your-key"
daysmart-mcp connect
daysmart-mcp status
daysmart-mcp serve
```

The bridge tools are `daysmart_guide`, `daysmart_status`, `daysmart_open`, `daysmart_read`, `daysmart_click`, `daysmart_type` and `daysmart_close`.

## Safety and scope

Bookings, appointment changes, voids and pickup texts ask for approval by default. No tool checks out a ticket, charges a card, changes payroll or deletes a client or pet. Pets, notes and vaccinations require DaySmart Pet. Failed calls are free. See the live [DaySmart integration page](https://cotlet.dev/integrations/daysmart-api-mcp-server) for the full operation and REST reference.

## License

Elastic License 2.0. Cotlet is not affiliated with DaySmart Software, LLC.
