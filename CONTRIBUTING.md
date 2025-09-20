# Contributing

Thanks for helping improve the Pokemon Tomy Database! This guide explains how to add or fix toy entries and how to organize images.

## Data model quick reference

Each Pokémon in `database.json` has a `toys` array of objects like:

```
{
  "id": "1_1",
  "notes": "Bulbasaur Tomy",
  "images": [
    "img/1_1/1_1-1.jpg",
    "img/1_1/1_1-2.jpg"
  ]
}
```

Key rules:

- Toy ID format: `<pokemon id>_<database id>` (e.g., `1_9` means Pokémon 1, variant 9)
- The `images` paths must match the repository folder structure: `img/<toy_id>/<toy_id>-<n>.jpg`
- Keep `notes` short but descriptive (pose, finish, color tone, etc.)

## Adding a toy

1. Determine the Pokémon's ID (e.g., 1 for bulbasaur) and the next available variant number for that Pokémon by scanning existing `toys`.
2. Create a new folder `img/<toy_id>/` (for example, `img/1_9/`).
3. Add one or more photos named `<toy_id>-1.jpg`, `<toy_id>-2.jpg`, etc.
4. Edit `database.json` and append a new toy object under the correct Pokémon entry.
5. Open a Pull Request using the "Add toy" template.

### JSON snippet example

```
{
  "id": "1_9",
  "notes": "Bulbasaur Clear Glitter Tomy",
  "images": [
    "img/1_9/1_9-1.jpg"
  ]
}
```

## Removing or fixing a toy

- If a toy is a duplicate or incorrect, remove the corresponding object from `database.json` and delete its `img/<toy_id>/` folder (or move images to the correct folder).
- Use the "Remove toy" PR template for removals, or open an issue using the "Problem with existing toy" issue template for corrections.

## Missing toys

If you can't submit a PR, please open an issue using the "Missing toy request" template. Include any references or photos you have.

## Style and validation

- Keep JSON valid and minimally formatted like the existing file.
- Filenames are lowercase and use the exact `<toy_id>-<n>.jpg` pattern.
- Do not hotlink external images inside `images`—store images in the repo under `img/`.

## Folder structure

```
img/
  <toy_id>/
    <toy_id>-1.jpg
    <toy_id>-2.jpg
```

## Thanks

Your contributions help collectors and fans keep an accurate index of Tomy figures. Thank you!
