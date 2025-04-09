# Kalm

- Breathing and meditation practice.

## Dev Logs

- Microsoft Edge's developer tool is pretty cool. When using width/height with arbitary px for my css animation, I got a warning in Edge's developer tool: `'height' changes to this property will trigger: 'Layout', which can impact performance when used inside @keyframes`. Hence, need to use `scale` to change the circle size. Chrome didn't show this warning tho. Maybe its time for a browser change lol.

- Currently using vanilla CSS, but I'm too lazy to think of CSS classname. So I'm thinking of using tailwind. However, this project will use bunch of css animation, tailwind classes will become too long. Fortunately, with Vue vscode extension, I can Ctrl + Click the classname in `template`, and it will bring me to the `style` definition. How convenient!. So I'll stick to vanilla CSS.
  - Just realized I used `classname` instead of `class`. Guess I'm doing too much React 🤣.

- Vue even got autocomple for css class that I defined in the component. :mindblown
  - Wait, where's the mindblown emoji? Guess when you're typing in the middle of the night, you'll mistakenly use :mindblown instead of 🤯.

## Reference
- Background image source: [Freepik](https://www.freepik.com/free-ai-image/ethereal-natural-environment_126077170.htm#fromView=search&page=1&position=15&uuid=7a35f597-7f66-4a07-adcd-d8a33e1a826c&query=Calm+Background)
  - Wanted to credit the author, but the image was generated by Midjourney. So... thanks AI?.