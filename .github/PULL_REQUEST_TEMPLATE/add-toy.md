---
name: Add toy
about: Propose adding a new toy entry and images
title: "Add: <pokemon name> <toy_id>"
labels: ["add-toy"]
---

## Summary

Describe the toy you are adding.

## Data changes

- Pokémon: <!-- e.g., bulbasaur (id 1) -->
- Toy ID: <!-- e.g., 1_9 (format: <pokemon id>_<database id>) -->
- Notes: <!-- short description, e.g., Clear glitter variant -->

## Files added

- database.json updated at path: `pokemon[<index>].toys[]`
- Images placed under: `img/<toy_id>/`
  - Filenames should follow: `<toy_id>-1.jpg`, `<toy_id>-2.jpg`, ...

## Checklist

- [ ] I followed the ID format `<pokedex>_<variant>` and used the next available variant number for this Pokémon
- [ ] I created a new folder `img/<toy_id>/` and added at least one image
- [ ] Image filenames match the pattern `<toy_id>-<n>.jpg`
- [ ] I updated `database.json` with the new toy under the correct Pokémon
- [ ] I verified JSON validity
- [ ] I updated the toy `notes` to be concise and descriptive

## Screenshots / references (optional)

Links or images that show the toy.
