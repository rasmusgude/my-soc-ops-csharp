# Copilot Workspace Instructions

## Development Checklist

Before finishing a code change, always:

- Run `dotnet build SocOps/SocOps.csproj`
- Run `dotnet test` when test projects exist
- Preserve existing Blazor component patterns and utility-class styling
- Avoid unrelated refactors or formatting-only changes

## Project Overview

Soc Ops is a Blazor WebAssembly app targeting .NET 10. It runs a social bingo game where players mark squares based on in-person prompts and win by completing a line.

## Project Structure

- `SocOps/Components`: reusable UI pieces such as the board, squares, modal, start screen, and game screen
- `SocOps/Pages`: routable pages; `Home.razor` is the main entry point
- `SocOps/Services`: gameplay state and bingo logic
- `SocOps/Models`: game state and board data types
- `SocOps/Data`: static bingo question content
- `SocOps/wwwroot`: static assets and the shared CSS utility system

## Commands

- Build: `dotnet build SocOps/SocOps.csproj`
- Run locally: `dotnet run --project SocOps/SocOps.csproj`
- Default dev URL: `http://localhost:5166`

## Blazor Guidance

- Keep page components thin and delegate stateful behavior to services
- Use dependency injection for services such as `BingoGameService`
- Prefer the existing event-driven update pattern over introducing parallel state systems
- Match existing Razor formatting and component parameter naming

## Styling Guidance

- Reuse the utility classes in `SocOps/wwwroot/css/app.css` before adding new CSS
- Keep CSS additions low-specificity and consistent with the existing utility naming scheme
- Follow the repo's design instructions in `.github/instructions/frontend-design.instructions.md` for UI-heavy changes

## State Management Notes

- `BingoGameService` owns the board, modal state, and game lifecycle
- `Home.razor` initializes the game service and subscribes to `OnStateChanged`
- Avoid duplicating game state in components when the service already owns it