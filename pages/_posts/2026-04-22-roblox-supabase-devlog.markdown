---
layout: post
title: "Devlog: Bringing Supabase Auth to Roblox"
date: 2026-04-22 14:30:00 +0900
categories: [devlog, luau, roblox]
type: Devlog
thumbnail: "/assets/images/blog/2026-04-22-roblox-supabase-devlog/thumbnail.png"
excerpt: "Notes on shipping the auth layer for Roblox-Supabase — token refresh, secure storage, and the quirks of HttpService."
---

Building a real backend integration inside Roblox is full of small surprises. This devlog captures the decisions I made while wiring up Supabase auth in Luau.

## Why a Luau client at all?

Roblox sandboxes the network heavily. `HttpService` is the only outbound channel, and it's restricted to server scripts. That means every auth flow has to be brokered through the server — there is no "client SDK" in the browser sense.

## Token storage

Tokens live in `DataStoreService` keyed by `UserId`. Refresh happens lazily on the first authenticated call after expiry, with a small jitter so we don't stampede the refresh endpoint.

## What's next

- Realtime subscriptions over WebSocket
- Storage uploads via signed URLs
- A typed query builder that mirrors the JS client

Stay tuned — the next devlog will cover the realtime piece.
