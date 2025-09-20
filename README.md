# Pokemon-Tomy-Database

A community-maintained, non-commercial database of all legitimate Pokémon Tomy toys and variants.

- Source data: [database.json](database.json)
- Contribution guide: [CONTRIBUTING.md](CONTRIBUTING.md)
- PR templates: [Add toy](.github/PULL_REQUEST_TEMPLATE/add-toy.md), [Remove toy](.github/PULL_REQUEST_TEMPLATE/remove-toy.md)
- Issue forms: [Missing toy](.github/ISSUE_TEMPLATE/missing-toy.yml), [Existing toy problem](.github/ISSUE_TEMPLATE/existing-toy-problem.yml)

## Goal

Document every legitimate Pokémon Tomy figure/variant with IDs, notes, and local images. Pull requests are accepted. Issues, reports, and requests should be made by creating a GitHub issue using the provided templates.

## Data structure

All data lives in [database.json](database.json).

Top-level shape:

- `version`: string (schema/file version)
- `pokemon`: array of Pokémon entries

Each Pokémon entry:

- `id`: number (Pokémon ID)
- `name`: string (lowercase)
- `types`: string[]
- `sprites`: object
	- `front_default`: string (URL to front sprite)
	- `back_default`: string or null (URL to back sprite)
- `toys`: array of toy entries

Each toy entry:

- `id`: string formatted as `<pokemon id>_<variant>` (e.g., `1_9`)
- `notes`: short description (pose, finish, color tone, etc.)
- `images`: array of local paths following `img/<toy_id>/<toy_id>-<n>.jpg`

### Sample

```json
{
	"version": "0.1",
	"pokemon": [
		{
			"id": 1,
			"name": "bulbasaur",
			"types": ["grass", "poison"],
			"sprites": {
				"front_default": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png",
				"back_default": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/back/1.png"
			},
			"toys": [
				{
					"id": "1_1",
					"notes": "Bulbasaur Tomy",
					"images": ["img/1_1/1_1-1.jpg"]
				},
				{
					"id": "1_2",
					"notes": "Bulbasaur Different Color Tone Tomy",
					"images": ["img/1_2/1_2-1.jpg"]
				},
				{
					"id": "1_3",
					"notes": "Bulbasaur Alternative Pose Tomy",
					"images": ["img/1_3/1_3-1.jpg"]
				},
				{
					"id": "1_4",
					"notes": "Bulbasaur Matte Alternative Pose Tomy",
					"images": ["img/1_4/1_4-1.jpg"]
				},
				{
					"id": "1_5",
					"notes": "Bulbasaur Clear Alternative Pose Tomy",
					"images": ["img/1_5/1_5-1.jpg"]
				},
				{
					"id": "1_6",
					"notes": "Bulbasaur Aduley Tomy",
					"images": ["img/1_6/1_6-1.jpg"]
				},
				{
					"id": "1_7",
					"notes": "Bulbasaur Sleeping Tomy",
					"images": ["img/1_7/1_7-1.jpg"]
				},
				{
					"id": "1_8",
					"notes": "Bulbasaur Battle Pose Tomy",
					"images": ["img/1_8/1_8-1.jpg"]
				}
			]
		}
	]
}
```

## Images folder structure

Local images must be stored under `img/` using this pattern:

```
img/
	<toy_id>/
		<toy_id>-1.jpg
		<toy_id>-2.jpg
		...
```

Rules:

- All-lowercase filenames.
- Use exact `<toy_id>-<n>.jpg` pattern.
- Do not hotlink external images inside `database.json`; store them locally in this repo.

## How to add a new toy

1. Find the Pokémon’s ID and the next available variant number for that Pokémon in [database.json](database.json).
2. Create a folder: `img/<toy_id>/` (e.g., `img/1_9/`).
3. Add one or more images named `<toy_id>-1.jpg`, `<toy_id>-2.jpg`, etc.
4. Edit [database.json](database.json) and append a new toy object under the correct Pokémon entry:

```json
{
	"id": "1_9",
	"notes": "Bulbasaur Clear Glitter Tomy",
	"images": ["img/1_9/1_9-1.jpg"]
}
```

5. Open a Pull Request using the [Add toy template](.github/PULL_REQUEST_TEMPLATE/add-toy.md). Validate JSON and file paths.

For more details, see [CONTRIBUTING.md](CONTRIBUTING.md).

## Pull requests and issues

- PRs are accepted for adding, fixing, or removing toys. Use:
	- [Add toy](.github/PULL_REQUEST_TEMPLATE/add-toy.md)
	- [Remove toy](.github/PULL_REQUEST_TEMPLATE/remove-toy.md)
- Report missing toys or problems via GitHub issues:
	- [Missing toy request](.github/ISSUE_TEMPLATE/missing-toy.yml)
	- [Problem with existing toy](.github/ISSUE_TEMPLATE/existing-toy-problem.yml)

## Credits

- Tomy Database: https://tomydatabase.weebly.com/
- Sprites and originaly entries are generated from PokeAPI.

## License

See [LICENSE](LICENSE).