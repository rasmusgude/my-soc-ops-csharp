# Copilot Workspace Instructions

## Development Checklist

Before finishing a code change, always:

- Run lint and fix issues; if no lint command exists, say so explicitly
- Run `dotnet build SocOps/SocOps.csproj`
- Run `dotnet test` when test projects exist

## Project Summary

Soc Ops is a .NET 10 Blazor WebAssembly social bingo app. Keep pages thin, put gameplay state in services, and avoid unrelated refactors.

## Working Rules

- `Home.razor` is the main page and subscribes to `BingoGameService.OnStateChanged`
- `BingoGameService` owns board state, modal state, and the game lifecycle
- Reuse `SocOps/wwwroot/css/app.css` utility classes before adding CSS
- Match existing Razor/Blazor patterns and use dependency injection for services
- Use `dotnet run --project SocOps/SocOps.csproj`; default local URL is `http://localhost:5166`