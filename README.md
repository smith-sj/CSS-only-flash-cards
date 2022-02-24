# CSS Only Flash Cards

Hosted here: https://smith-sj.github.io/CSS-only-flash-cards/

The title pretty much says it all, I decided to put my recently aquired CSS knowledge to the test by creating some functional flash cards using only CSS. As we were also learning about HTTP, it felt like a fitting theme for the project. The term *“mobile first”* was also thrown around a lot in class this week, so I set out to make this project functional on mobile first and then adjusted for desktop. 

## What are some cool things I learned?

- Flexbox layout
- Building Mobile First
- The power of the `calc()` CSS function
- The ***Checkbox Hack*** *(which is fun but not appropriate most projects)*


## What were some challenges I faced?

- Making mobile first layouts and CSS animations that would translate well to desktop
- Discovering the different ways each mobile browser treats the :hover pseudo-selector

## PART 1: General Layout and Animation

This project started off pretty smoothly. There were a few bumps as I adjusted to the idea of using dynamic sizing units such as `vw` and `vh`, but after a bit of experimentation (and remembering to use CSS’s `calc()` function,) things started to make sense. Thanks to learning flexbox, I felt like I could finally implement whatever layout popped into my head.

I have to admit, learning CSS animation was easier than I thought it would be, that said, this project uses some pretty basic ones. There are the initial fanout `@keyframes` for each card, that activate when the page loads and are responsible for the cards moving to their initial positions and then their are the `transform` rules that are activated on hover (this was eventually changed to on-tap, but we’ll get to that later.) Turns out CSS keyframes are really quite simple and they really just work.

I found the most challenging part to be translating the layout and animations from mobile to desktop. I ended up using dynamic sizing units for mobile and static sizing for desktop, it just ended up being easier but did feel like I was cheating a little bit. If I find some spare time during this crazy bootcamp, I’d like to refactor the desktop layout to use dynamic sizing as well.

## PART 2: The Hover Dilemma and Discovery of CSS Hacks

I now had a pretty cool deck of cards that fanout and then pop up when you hover over them. As I was using Chrome developer tools in mobile layout, the hover effect translated pretty smoothly. I just tapped (clicked) a card and it would pop up and if I tapped another card it would pop up and the other would pop down. The only issue was that you couldn’t tap the card to go back down. I was okay with that. So I pushed it up to GitHub, deployed it to pages, checked it on my Android phone Chrome and bam! It worked beautifully. Then I grabbed my partner’s iPhone, opened it up in Safari and *”… oh.. No, what is this!?”* Safari treats hover differently! And in this case, it was horrible. On Safari you have to hold the card for a second to activate the hover effect, but since the only place to click the card was text, it would select the text and you’d have this weird highlighted nothingness. The whole experience just felt off. I could probably have fixed the text selection problem. But the feeling of having to hold the cards was just bad in general. Since most people will probably view this project with mobile Safari, this just wasn’t going to cut it.

Then my bro came to the rescue. Yes, my actual brother, Derrick Yearnsmith,  CSS veteran and all-round talented dude. He told me about these *CSS Hacks* - some sort of ancient art, the kind of which would probably not be taught in a respectable bootcamp, but are known by the bravest of coders. The 3 that he mentioned were the ***Anchor Hack***, ***Checkbox Hack*** and ***Radio Button Hack***, and as he warned *“they’re very hacky, and should be avoided, but might be good for your fiddle”* or something like that. Yes they were hacky, and yes, I tried all of them. I won’t go into how they all work because *"Google"*, but I will tell you why I went with the ***Checkbox Hack*** in the end. The Anchor Hack was messy - it worked, but it caused the page to jump as it implements the `:target` pseudo-class selector. The Radio Button Hack wasn’t messy, it worked, but it had the one drawback of not allowing you to tap a card back down, as is the case with radio buttons, the only way to deselect one is to select another. So the Checkbox Hack won.

In a nutshell, the card’s main container is a `label` with the `for` attribute set to an input, one line above. The input type is set to `checkbox` and the `hidden` attribute is added, so the checkbox is invisible. Then over in CSS land, the `:checked` pseudo-class selector is combined with `+ #cardID` to select the appropriate label. The rule can then be whatever needs changing, in this case: the label’s transform.

The result is smooth, functional and very hacky.

## Conclusion

I learned a lot from doing this little project, and as a bonus I also got more comfortable with using branching and merging in git. I could use this as some sort of menu on a portfolio site or something, but due to its lack of accessibility I should probably wait to learn JS and implement it in a more modern way.
