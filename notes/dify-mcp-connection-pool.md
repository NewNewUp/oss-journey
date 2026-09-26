PR #42658. Every MCP tool invocation opened a connection and closed it when the
call returned. Stateful servers (Playwright MCP!) lost everything: navigate,
then screenshot, and the browser was back to about:blank.

Fix: a process-wide MCPClientManager. Pool key = stable scope (tenant + user +
provider + server), never per-call credentials (forwarded tokens are minted per
call; OAuth tokens rotate — keying on them prevents all reuse). Two-level locks
with a doomed-entry handoff so one hung call cannot wedge the whole registry.
Idle TTL + LRU cap + single reconnect retry on dead connections.

Review lesson: my first version held the registry lock while waiting on a
per-connection lock that an in-flight call held indefinitely. The reviewer's
repro hung every tenant on one stuck Playwright call. Lock ordering is a
feature, not a detail.
