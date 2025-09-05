# Pokedex

A simple Go CLI Pokedex that lets you explore locations, catch Pokémon, and inspect your collection using data from the PokeAPI.

## Features
- `help`: List available commands
- `map` / `mapb`: Navigate paginated location areas
- `explore <location-area>`: List wild Pokémon in an area
- `catch <pokemon>`: Attempt to catch a Pokémon and store it locally
- `inspect <pokemon>`: Show name, height, weight, stats, and types (only if caught)
- `exit`: Quit the REPL

## Installation
- Requirements: Go >= 1.21
- Clone and build:
  ```bash
  git clone https://github.com/davutkulaksiz/pokedex
  cd pokedex
  go build -o pokedex
  ```
- Run:
    ```bash
    ./pokedex
    ```

## Usage
```bash
Pokedex > help
Pokedex > map
Pokedex > explore route-1
Pokedex > catch pidgey
Pokedex > inspect pidgey
Pokedex > exit
```

## Architecture
- `main.go` / `repl.go`: REPL loop and command dispatch
- `command_*.go`: Individual command implementations
- `internal/pokeapi`: HTTP client and typed responses to PokeAPI
    - `pokemon_get.go`, `location_list.go`, `location_get.go`
- `internal/pokecache`: In-memory cache with TTL to avoid redundant API calls

## Data Source
- Uses [PokeAPI](https://pokeapi.co/)

## Inspect Behavior
- `inspect <name>` prints details only for Pokémon you’ve caught.
- No extra API call is needed—details are stored at catch time.

## Testing
- Run tests:
    ```bash
    go test ./...
    ```

## Limitations / Future Work
- Persistent storage (save caught Pokémon across runs)
- Better catch probability mechanics
- Richer error messages and input validation
- More commands (release, list, stats summaries)