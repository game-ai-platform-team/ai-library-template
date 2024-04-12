# ai-library-template

This template contains CI/CD workflows and invoke tasks for an AI library.

## Configuration

Add following items to repository secrets:
|Name|Where to get it|
|-|-|
|`CODECOV_TOKEN`|[Codecov](https://docs.codecov.com/docs/adding-the-codecov-token)|
|`PYPI_TOKEN`|[PyPI](https://pypi.org/help/#apitoken)|

## What I need for an AI?

You need to implement at least the following classes from [duo-game-lib](https://github.com/game-ai-platform-team/duo-game-lib):

- `Player`, represents the AI
- `Judge`, responsible for game rules

## How to add AI to tira-ai-platform?

1. Create new repository from this template
1. Implement the AI
1. Deploy the package to PyPI with deployment workflow
1. Add AI library to [tira-ai-platform](https://github.com/game-ai-platform-team/tira-ai-platform)

   ```sh
   poetry add ai-library-name
   ```

1. Add factory method for the AI in `PlayerFactory`
1. Add factory method for the game with `Judge` class in `GameFactory`

## Architecture

The relations between duo-game-lib classes can be found in [architecture document](https://github.com/game-ai-platform-team/tira-ai-platform/blob/main/docs/architecture.md#backend) of the main project.
[connect-four-lib](https://github.com/game-ai-platform-team/connect-four-lib/blob/main/docs/architecture.md) can be used as an example for an AI library.

## Deployment

- Update `version` in `pyproject.toml`, use semantic versioning
- Run "Deploy" workflow manually in GitHub Actions

> [!IMPORTANT]
> Before publishing the package to PyPI:
>
> - Add repository secrets required in configuration
> - Rename directory `src/name_of_ai_lib` to a desired name and update `packages` in  `pyproject.toml`
> - Change `name` in `pyproject.toml`
