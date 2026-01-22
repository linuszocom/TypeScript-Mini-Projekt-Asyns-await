```typescript
import type { Song } from "../models/Song.js";

export const getPlaylist = async (): Promise<Song[]> => {
  const response = await fetch("./songs.json");

  if (!response.ok) {
    throw new Error(`HTTP ERROR: ${response.status}`);
  }

  const data = (await response.json()) as Song[];

  return data;
};
```

```typescript
async function initApp() {
  console.log("Initiera appen, hämtar data...");

  try {
    const apiSongs = await getPlaylist();

    playlist.push(...apiSongs);

    renderSongs("song-list-container", playlist);
  } catch (error) {
    console.error("Fel", error);
  }
}
```
