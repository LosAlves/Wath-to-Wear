[README.md](https://github.com/user-attachments/files/35231991/README.md)
# What should I wear? 👕🌦️

A simple, picture-based web app that helps a young child choose what to wear each day, based on the weather. One screen, one question, big pictures and a friendly voice.

**Languages:** English · Français · Português (Portugal), plus an *Automatic* option that follows the device language.

## Features

- **Live weather** from [Open-Meteo](https://open-meteo.com/) (free, no API key), using the device's approximate location.
- **Today or Tomorrow:** pick which day to dress for. Tomorrow uses the forecast's daytime "feels like" high.
- **Outfit of the day:** an overview of everything to wear, then one item at a time with a big "I put it on" button.
- **Animated backgrounds** that match the weather: sun, clouds, rain or snow. Respects *Reduce Motion*.
- **Voice:** spoken instructions using the device's built-in voices, with a mute button and a voice picker. The voice stops whenever the screen changes.
- **Temperature units:** °C or °F.
- **Fallback:** if the weather can't load (location blocked, offline), a coloured thermometer scale lets a grown-up choose the temperature and sky by hand.
- **Grown-up override:** on the weather screen, press and hold the weather card for about 1.5 seconds to open the thermometer and correct the forecast.
- **Privacy first:** no accounts, ads, analytics or tracking. See [privacy.html](privacy.html).

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app (HTML, CSS and JavaScript in one file) |
| `privacy.html` | Privacy policy (English and French) |
| `README.md` | This file |

## Put it online with GitHub Pages

1. Keep `index.html` at the top level of the repository.
2. Open **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, then **main** and **/ (root)**, and save.
4. After about a minute, open `https://YOUR-NAME.github.io/REPO-NAME/`.

Location needs a secure page (https), so test on the Pages link rather than on a local file. On an iPhone or iPad, tap **Share → Add to Home Screen** to open it like an app.

## How the outfit is chosen

Temperatures are "feels like" values in °C. The manual thermometer works in steps of 5° (30° down to -5°).

| Situation | What changes |
|---|---|
| Hot (25° and above) | Light T-shirt, shorts, sandals |
| Nice (13° to 24°) | T-shirt or sweatshirt, long trousers, sneakers and socks |
| Cold (below 13°) | Sweatshirt and thick fleece sweater, warm coat, scarf, gloves, warm hat, boots, warm socks |
| 5° and below | Warm trousers |
| Sunny or cloudy | T-shirt from 20°; sweatshirt below 20° |
| Sunny | Sunglasses from 25°; sun cap above 15° |
| Rain below 20° | Sweatshirt, rain boots, raincoat, umbrella |
| Rain 20° and above | T-shirt, raincoat only; choose shorts or light summer pants; from 25°, choose sandals or sneakers and socks |
| Cloudy 20° and above | Choose shorts or light summer pants |
| Snow (only below 5°) | Sweatshirt, snow boots, warm coat, scarf, gloves, hat |

To change these rules, edit the `outfit()` function in `index.html`. Clothing names live in the `T` translation block, and the thermometer steps are in `TEMPS`.

## Privacy in one paragraph

If you tap **Weather**, the device asks for permission to use its location. The app then sends approximate coordinates (rounded to about 1 km) to Open-Meteo to get the weather. Nothing is stored on a server. Language, unit, mute and voice choices stay on the device. The full policy is in [privacy.html](privacy.html). Fill in the contact details there before publishing.

## Build it as an iOS app (optional)

The page can be wrapped with [Capacitor](https://capacitorjs.com/) and published on the App Store. You need a Mac with Xcode and an Apple Developer account.

```bash
npm install @capacitor/core @capacitor/cli @capacitor/ios
mkdir www            # copy index.html into www/
npx cap init "What to wear" com.yourname.whattowear --web-dir www
npx cap add ios
npx cap sync ios
npx cap open ios
```

In Xcode, add `NSLocationWhenInUseUsageDescription` to the app's Info settings, choose your Team under *Signing & Capabilities*, then run and archive. After editing `index.html`, copy it into `www` and run `npx cap sync ios` again.

## Credits

- Weather data: [Open-Meteo](https://open-meteo.com/) (open data, free for non-commercial use; check their terms for commercial use).
- Emoji pictures come from the device's emoji font. The sweater, sweatshirt, beanie and summer pants are drawn as SVG inside the page.

## License

Add a license of your choice (for example MIT) as a `LICENSE` file.
