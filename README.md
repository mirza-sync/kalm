# Kalm
- Breathing and meditation practice.

## Dev Logs

- Microsoft Edge's developer tool is pretty cool. When using width/height with arbitary px for my css aniation, I got a warning in Edge's developer tool: `'height' changes to this property will trigger: 'Layout', which can impact performance when used inside @keyframes`. Hence, need to use `scale` to change the circle size. Chrome didn't show this warning tho. Maybe its time for a browser change lol.

- Currently using vanilla CSS, but I'm too lazy to think of CSS classname. So I'm thinking of using tailwind. However, this project will use bunch of css animation, tailwind classes will become too long. FOrtunately, with Vue vscode extension, I can Ctrl + Click the classname in `template`, and it will bring me to the `style` definition. Pretty cool!. So I'll stick to vanilla CSS.
    - Just realized I used `classname` instead of `class`. Guess I'm doing too much React 🤣.