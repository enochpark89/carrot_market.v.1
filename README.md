# Carrot market

# Key Terms
pages/index.tsx: This is where the page is displayed.


# Requirement



# Install Tailwind
```
npm install -D tailwindcss postcss autoprefixer
```
- It should show on the dev dependencies of package.json file. 

*Initiate tailwindcss*:
```
npx tailwindcss init -p
```
- Creates postcss.config.js and tailwind.config.js files.

- Update tailwindconfig.js to tell them where the tailwind is going to be used. 
```js

```

# Tailwind

## 1. Introduction

*Benefit:*
**

*What is Tailwind*
- Tailwind is a utility-first CSS framework with classes like flex, pt-4, text-center etc.

- Options you can use:
Grid, flex, font-size, font-style, 

- Install tailwind CSS intellisense if you want recommendations popping up.

## 2. TailwindCSS workflow

- It is not easy to start in the beginning because you have to look at the documentation and come back. However, it will get easier along the way.

- Class names:
    - border: creates a border
    - font: change font sylte 
    (ex: - font-semibold, font-medium)
    - rounded: create a rounded corners.
        - rounded-full: make square into a circle.
    - flex, flex-col, 
    - relative movements - margin-top minus.

## 3. inputs

More classes:
- overflow-hidden
- input button
- space-x-3: Utilities for controlling the space between child elements.
(could be applied to flex.)

- font-medium(font-weight) vs text-ul (font-size)
- aspect-square: helps us using ratio and make it a perfect square.

Helper class gives shorcuts.
- ring: space-x-5 we get calculation

## 4. Helper functions

Classes:
w: width
h: height

Helper Classes:
- When you put your mouse over, you want the button to change.
hover: bg-teal-500

- You want the button to change when the button is focused or selected.
focus: bg-red-500

## 5. Transition

- Ring utility: This is not a modifier but you can mix with a modifier to create a cool effect. 
- Focus modifier + ring utility can create a color button that can be clicked and be focused. 
```html
<button className="w-5 h-5 rounded-full bg-yellow-500 focus:ring-2 ring-offset-2 ring-yellow-500 transition" />
```
- This creates a ring around the circular button.

- You can change the ring color by changing the ring opacity.
bg-opacity-20
- Tip: put your mouse over to see what you can do with the properties.

## 6. Modifiers for Lists

- When you are iterating through an arry to display html tags as below, you can use first: and last: to target the first and the last child element. 

```html
<ul>
    {[1, 2, 3, 4].map((i) => (
    <div
        key={i}
        className="flex justify-between my-2 odd:bg-blue-50 even:bg-yellow-50 first:bg-teal-50 last:bg-amber-50"
    >
        <span className="text-gray-500">Grey Chair</span>
        <span className="font-semibold">$19</span>
    </div>
    ))}
</ul>
```
Other selector:
even:, 
odd;, 
empty:hidden

*What if you want to hover your mouse over the container rather than a button?*

You have to use a **Group Selection**

## 7. Modifiers for Forms

```css
.group:hover .avatar {

}
```
- We can accomplish group selection with TailwindCSS. 

Step 1:
1. Tell TailwindCSS the group that you want to target. 
- Add a classname called group.
2. Then, you tell how the group will respond, when the event happends.

```
```

*How do you apply the normal CSS inside the TailwindCSS?*

- focus-within:bg-blue-500.
- placeholder-shown:bg-teal-500: display placeholder if placeholder is visible. 
- There are many of them. 

*How do you disable inputs?*

- disabled:opacity-0
- invalid: bg-red-500.

*Peer modifier*
- input is the peer. mark it as a peer. 
- item next to it, when the peer is invalid, it will take the signal and display the message. 
- This is just exposed nice API from TailwindCSS but this is actually a CSS function.
peer:valid, peer:invalid
- This is using sibling selector. 

## 8. More modifiers

HTML tag that are there. 
```html
<details>
    <summary>
        What is my favorite food.
    </summary>
    <span>
        Hello
    </span>
</detail>
```
- You can toggle between showing and not showing of a span.
- select-none cursor-pointer.
- selection:bg-indigo-600 - allows the change of color when the user is selecting it. 

*How do you modify how to list looks?*
```html
<ul className="list-decimal marker:text-teal-5">
    <li>hi</li>
    <li>hi</li>
    <li>hi</li>
</ul>
```
- change the list to decimal, and other options. 

*Change the input file*
- if you use the file modifer, you can change the border.r 
file: border-0 file:rounded. 
- you are using a file modifier because you are aiming for the file button.l 

- You can stack many modifiers together
```
    <div className="flex flex-col space-y-2  p-5 ">
      <p className="first-letter:text-7xl first-letter:hover:text-purple-400">
        Hello everyone!
      </p>
    </div>
```
file:cursor-waiting
file:transition-colors
file:hover:text-purple-400
file:hover:bg-white
file:hover:border
etc.
first-letter:text-7xl - select the first letter and make it bigger. 

## 9. Responsive Modifier

- People usually think about the desktop but TailwindCSS starts with the mobile and it adds on to build a desktop. 

- starts with white and it changes as the screen gets bigger
```html
<div className="bg-white" sm:bg-red-400 md:>
```

- Add three columns to the grid. 
- How do you create a grid-column: grid-col.
    - if you want to place the element or maximize the column, you use grid-col-span

- col-span-1
- xl:col-span2; xl:col-span1
- Another query: orientation.
- 

# 4.11. Dark Mode

- Dark Mode is easy with TailwindCSS.
- If the user has a dark mode.
- All you need to do is to add below
```
dark: bg-black
```
- This will select which color that it will be when the user select the dark mode. 

- This is listening to the preferences of the browser.
- If you do not want to follow the browser, you can do that by changing the tailwind config file. 
tailwind.config.js:
```
darkMode: "media" or "class
```

Conclusion:
1. tailwind.config.js > modify darkMode to media
2. You put the darkMode class by using dark:

# 4.12 Just in Time Compiler

- TailwindCSS is a large CSS file but there are more to it. 
- If you are able to group like the modifier, the CSS would be too big. 
- Tailwind CSS 3.0 introduces Just-In-Time complier to reduce the size of the CSS or to clean the file. 
- We used to do "purging" before we publish to the website which scan all the files and only keep the ones that we are going to use. 
- We can now stack modifiers after modifiers. It watches your classes and create on-demand. 
- In other words, you are only compling the ones that you use from the @Tailwind modules because you don't need it if you don't use it. 

- The best part is sometimes you want to get out of the restriction of the TailwindCSS. JIT, you can set the text bigger
text-[9874px] instead of the default fonts. 
bg-[url('/vercel.svg')]"]

