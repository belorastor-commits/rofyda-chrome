# ROFYDA CHROME
### Digital Save The Date Website · Setup Guide

Welcome, and congratulations.

Everything you change lives in one place. You will not need to write code,
and you will not need to hunt through the file. Set aside about twenty
minutes.

---

## What you received

```
rofyda-chrome/
├─ index.html      your whole website, in a single file
├─ images/         your photos go in here
└─ README.md       this guide
```

---

## Before you start

**See it working first.** Double-click `index.html`. It opens in your
browser. Press the envelope to open it, then scroll through.

The demo shows Olivia and Noah in Florence. Every one of those words is
yours to replace.

Where a photo has not been added yet you will see a soft ivory panel with a
small chrome mark. That is the finished empty state, not a fault. It looks
intentional, so you can share the site with family while you are still
choosing pictures.

**To edit**, right-click `index.html` → Open with → Notepad on Windows, or
TextEdit on Mac. If you would like something easier on the eye, VS Code is
free and colours the text so the parts you edit stand out.

**The golden rule.** Change only the words between the quote marks. Leave
every comma, colon and quote mark exactly where it is.

```
nameOne:"Olivia",        →     nameOne:"Fatima",
```

Save the file, then refresh your browser. If the page ever goes blank, a
quote mark or comma was removed by accident — press Ctrl+Z (Cmd+Z on Mac)
until it comes back.

---

## The configuration

Open `index.html` and search for **ROFYDA CONFIG**. Everything described
below is inside that block.

### The couple

| Setting | What it does |
|---|---|
| `nameOne` | First name, shown on the envelope, the card and the hero |
| `nameTwo` | Second name |
| `joiner` | The word between them. `"and"`, `"&"`, `"et"` — your choice |

### The date

| Setting | What it does |
|---|---|
| `dateISO` | **Drives the countdown.** Must look exactly like `2027-09-24T16:00:00` |
| `dateLong` | Written out: `"24 September 2027"` |
| `dateStamp` | Short form on the envelope: `"24.09.2027"` |

`dateISO` is the only setting with a strict shape: four-digit year, dash,
two-digit month, dash, two-digit day, the letter **T**, then the time on a
24-hour clock. The countdown updates every second on its own, and on the
day itself it changes to the words in `dayOfMessage`.

### The invitation wording

| Setting | What it does |
|---|---|
| `invitation` | The short passage under your names |
| `storyTitle` | Heading of the story section |
| `story` | Your story, as a list. Each entry becomes a paragraph |
| `dayOfMessage` | Replaces the countdown once the day arrives |
| `closing` | The final line of the site |

To add a third paragraph, copy an existing line and keep the commas between
entries:

```
story:[
  "First paragraph.",
  "Second paragraph.",
  "Third paragraph."
],
```

### Ceremony and reception

Two separate blocks, `ceremony` and `reception`, each with the same four
settings:

| Setting | Example |
|---|---|
| `time` | `"4:00 in the afternoon"` |
| `venue` | `"Chapel of San Lorenzo"` |
| `address` | `"Via delle Terme 14, Florence, Italy"` |
| `mapUrl` | The link behind **View on map** |

### The venue section

The `venue` block has five settings: `name`, `address`, `time`,
`directions` and `mapUrl`. `directions` is the longer paragraph about
trains, parking and travel.

### Dress code

`dressCode` is the large italic line. `dressNote` is the sentence beneath
it.

### Map links

There are three: `ceremony.mapUrl`, `reception.mapUrl` and `venue.mapUrl`.
Each arrives holding a reminder:

```
https://maps.google.com/?q=REPLACE+WITH+YOUR+VENUE
```

To replace one: open Google Maps, search for your venue, press **Share**,
copy the link, paste it between the quote marks. Repeat for all three — or
paste the same link into all three if everything happens in one place.

---

## Your photos

Put your picture files in the `images` folder, then write each filename
into the `images` block. You may name the files anything you like.

```
images:{
  story:"us-in-rome.jpg",
  storyDetail:"rings.jpg",
  venue:"the-villa.jpg",
  gallery:["one.jpg","two.jpg","three.jpg","four.jpg","five.jpg"]
},
```

| Slot | Where it appears | Shape | Pixel size | Keep under |
|---|---|---|---|---|
| `story` | Tall portrait in the story section | 3:4 | 1200 × 1600 | 350 kb |
| `storyDetail` | Smaller picture beneath it — **optional** | 4:3 | 1200 × 900 | 250 kb |
| `venue` | Wide picture above the venue details | 4:3 | 1600 × 1200 | 350 kb |
| `gallery[0]` | First and widest in the gallery | 3:4 | 1000 × 1300 | 200 kb |
| `gallery[1]` – `gallery[4]` | The remaining four | 3:4 | 1000 × 1300 | 200 kb each |

Two things worth knowing.

**The frame decides the crop, not your file.** Whatever shape your picture
is, it fills its frame from the centre and the layout never moves. You do
not need to crop anything beforehand, though centring your subject helps.

**Size matters more than you would think.** A photo straight from a modern
phone can be four megabytes. Guests will open your site standing in a field
with one bar of signal. Shrink your pictures to the sizes above and the
site opens instantly for everyone.

Any slot left as `""` shows the quiet ivory panel. Leaving `storyDetail`
empty is a perfectly good design choice.

### The sharing picture

When you send your link by message, most apps show a preview. That comes
from a file named `share.jpg` in the `images` folder, sized **1200 × 630**.
If you do not add one, the link still works — it simply shows no preview
image.

---

## Replies from your guests

```
rsvp:{
  enabled:true,
  endpoint:"",
  method:"POST",
  email:"olivia.and.noah@example.com",
  deadline:"Kindly reply by 1 July 2027"
},
```

| Setting | What it does |
|---|---|
| `enabled` | `true` shows the RSVP section. `false` removes it completely, along with its link in the menu |
| `endpoint` | Where replies are sent, if you connect a form service |
| `method` | Leave as `"POST"` unless your form service asks for something else |
| `email` | Your address, used while `endpoint` is empty |
| `deadline` | The line above the form |

### Two ways it can work

**Straight out of the box — nothing to set up.** Leave `endpoint` as `""`
and put your own address in `email`. When a guest fills in the form and
presses **Submit RSVP**, their email app opens with their answer already
written out. They press send, and it arrives in your inbox.

This works immediately and needs no account anywhere. Its limit is that
replies arrive as separate emails rather than as one tidy list.

**Collecting replies in one list — optional.** If you would rather see every
reply in a single table, create a form with a service that accepts
submissions from a website, and paste the address it gives you into
`endpoint`:

```
endpoint:"https://example-form-service.com/f/your-id",
```

Nothing else changes. Each reply then goes straight to that service, and
your guest sees:

> **Thank you.**
> We can't wait to celebrate with you.

**An honest note.** Nothing is stored anywhere unless you connect a service
yourself. This site has no database of its own and does not quietly keep
your guests' answers. Until you add an `endpoint`, replies travel by email
and nowhere else.

---

## Wording

The `text` block holds every heading and button on the site. Change these
only if you want different words — or the entire site in another language.

| Setting | Default |
|---|---|
| `heroKicker` | The invitation |
| `cardKicker` | Save the date *(on the card inside the envelope)* |
| `detailsLabel` | The day |
| `ceremonyLabel` | Ceremony |
| `receptionLabel` | Reception |
| `countdownLabel` | Counting down |
| `storyLabel` | Our story |
| `galleryLabel` | Moments |
| `rsvpLabel` | Reply |
| `rsvpHeading` | We would love to celebrate with you |
| `venueLabel` | The venue |
| `dressLabel` | Dress code |
| `mapButton` | View on map |
| `submitButton` | Submit RSVP |
| `thankYou` | Thank you. |
| `thankYouSub` | We can't wait to celebrate with you. |
| `footer` | Rofyda · Modern Digital Wedding Invitations |

---

## The envelope

```
openLabel:"Tap to open",
envelope:{
  paperColor:"",
  flapColor:"",
  cardColor:"",
  sealColor:"",
  monogram:"",
  speed:1
},
```

| Setting | What it does |
|---|---|
| `openLabel` | The words beneath the envelope |
| `paperColor` | The envelope body. Leave `""` to follow your theme |
| `flapColor` | The flap that opens |
| `cardColor` | The card that rises out |
| `sealColor` | The round seal |
| `monogram` | What the seal says. Leave `""` and it uses your two initials |
| `speed` | `1` is normal. `0.7` is quicker, `1.4` is slower |

To use a colour of your own, write it as a hex code:
`paperColor:"#EFE9DE"`. Leaving all four empty is recommended — they then
stay in step with your chosen theme automatically.

---

## Choosing a look

At the very top of the configuration:

```
theme:"chrome",
```

Replace the word with any of these five. The whole site changes at once.

| Theme | Character |
|---|---|
| `chrome` | Warm ivory, deep burgundy, champagne — the original |
| `burgundy` | Warmer and rosier throughout |
| `ivory` | Softest and palest, with a muted gold |
| `black` | Dark paper with brass. Striking for evening weddings |
| `editorial` | Cool grey paper with ink blue. The most modern |

Try each one. It takes two seconds and costs nothing.

---

## Music

```
audioUrl:"",
```

Leave it empty for silence. To add music, put an `.mp3` file in the same
folder as `index.html` and write its name: `audioUrl:"our-song.mp3"`. A
small round button then appears in the corner.

Music never starts on its own — your guest chooses to press play. Phones
block automatic sound anyway, and a site that plays music unexpectedly in a
quiet room is a site people close.

**Please only use music you hold the rights to use.** Commercially released
songs are not free to publish on a website, even a private one.

---

## Putting your site online

1. Go to **app.netlify.com/drop**
2. Drag your whole `rofyda-chrome` folder onto the page
3. A live link appears within seconds

In the site settings you can rename it to something like
`olivia-and-noah.netlify.app`. That is the link you send to your guests.

Any ordinary web host works just as well. The site is one folder of plain
files with nothing to install.

---

## On phones and computers

This site was built for the phone first, because that is where nearly every
guest will open it.

It has been checked at **360, 390 and 430 pixels** wide — covering current
phones from the smallest upward — and at **768, 1024 and 1440** for tablets
and computers. Nothing scrolls sideways, no text is cut off, and the
countdown keeps all four figures on one line even on the narrowest screen.

Guests who have switched on the reduced-motion setting on their phone see
the same site with the animation stilled. Nothing is lost.

**One thing to check yourself:** open your finished site on a real phone
before you send it out. Look at your longest name on the opening screen,
and at your photos in the gallery.

---

## If something looks wrong

**The page is blank.** A quote mark or a comma was removed. Undo until it
returns, then make the change again more carefully.

**A photo is not showing.** The filename in the configuration must match
the file exactly, including capital letters and the `.jpg` ending. If they
do not match, the quiet ivory panel appears instead — the page still looks
right, but your picture will not be there.

**The countdown shows a note about dateISO.** The date is not in the
required shape. It must look exactly like `2027-09-24T16:00:00`.

**A map button goes nowhere.** That link still holds the
`REPLACE+WITH+YOUR+VENUE` reminder.

**The seal shows the wrong letters.** Set `envelope.monogram` to whatever
you would prefer.

---

Rofyda · Modern Digital Wedding Invitations & Experiences
