# Password Cypher

One secret phrase you remember + the website's name = a strong, unique password for every site.

Forget a password? Open the page, type your phrase and the website again, and the exact same password comes back. Nothing is stored or sent anywhere, so there is no password list that can be hacked.

## How to use it

1. Open `index.html` in any web browser (double-click it). It works with no internet.
2. **Your key:** type your master phrase (four or more random words is best). Pick which characters to use and the length, then never change these.
3. Note your **key check** (for example "Violet Turtle 85"). If it ever shows something different, you mistyped your phrase.
4. **The website:** type the site name or paste its web address. `https://www.amazon.com/login` and `amazon.com` give the same password.
5. Copy the password and paste it into the site.

## When a site gets hacked or asks for a new password

Raise that site's **version** from 1 to 2 and you get a brand-new password for that site only. Press "Remember this site's settings" so the page remembers the version for you. You can also write the "recipe" line down, since it contains nothing secret.

## How it works (technical)

- PBKDF2-SHA256 with 300,000 rounds, using the master phrase as the key and the site, username, version and rules as the salt.
- The result seeds an HMAC-SHA256 byte stream that picks characters without bias and always includes at least one of each chosen character type.
- Everything runs in the browser's built-in Web Crypto. Only non-secret settings (site, version, length) are ever saved, in the browser's local storage.

**Important:** the formula is fixed. If the code's recipe constants change, every password changes, so don't edit them.
