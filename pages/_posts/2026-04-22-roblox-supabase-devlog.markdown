---
layout: post
title: "Roblox-Supabase: A Type-Safe Supabase Client for Roblox"
date: 2026-04-22 14:30:00 +0900
categories: [project, typescript, roblox]
type: Project
thumbnail: "/assets/images/blog/2026-04-22-roblox-supabase-devlog/thumbnail.png"
excerpt: "An overview of Roblox-Supabase — a type-safe library that lets Roblox games talk to a Supabase backend directly from roblox-ts."
---

[Roblox-Supabase](https://github.com/Waffle0823/Roblox-Supabase) is a library that brings modern backend capabilities to Roblox experiences. It gives you a **type-safe way to interact with your Supabase backend** — auth and database today, with more on the roadmap — straight from the [roblox-ts](https://roblox-ts.com/) ecosystem.

## What it is

Roblox has no browser-style client SDK, and `HttpService` is the only outbound channel. Roblox-Supabase wraps that reality in a clean, typed API so you can query your Supabase project as if you were using the official JavaScript client.

## Features

- **Type-safe PostgREST client** for reading and writing your database
- **TypeScript-first design**, built on roblox-ts
- **Authentication** handling for secure API access
- **Type generation** via the Supabase CLI, so your schema types flow all the way into Luau
- A **simple query API** that mirrors the standard Supabase client

## Installation

```bash
npm install @rbxts/roblox-supabase
```

## Usage

Initialize the client with your project URL and anon key. Keep the key out of source using `HttpService.GetSecret`:

```ts
import { SupabaseClient } from "@rbxts/roblox-supabase";

const supabase = new SupabaseClient(
    "https://your-project.supabase.co",
    HttpService.GetSecret("SUPABASE_ANON_KEY"),
);
```

## Tech stack

**TypeScript** · **roblox-ts** · **Supabase** · **PostgREST**

## Status

The project is in **alpha** — the API surface may still change. Realtime subscriptions and Storage support are planned next. Contributions and issues are welcome on [GitHub](https://github.com/Waffle0823/Roblox-Supabase).
