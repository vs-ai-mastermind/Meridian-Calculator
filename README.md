# Meridian Calculator

A single-file, offline anisometropia calculator. Enter the spectacle prescription for each eye and it finds the meridian where the two eyes differ most in power, and how large that difference is.

## Usage

1. Open `MeridianCalculator.html` just as you would open any file on your computer in any modern browser. There is nothing to install or build, and no network access is needed.
2. Enter **sphere**, **cylinder** and **axis** for OD (right) and OS (left).
   - Sphere and cylinder are in diopters (D). Use plus or minus cylinder, but use the same form for both eyes.
   - Axis is in degrees, 0–180.
3. Results update as you type.

## What it shows

- **Greatest anisometropia**: the largest absolute power difference between the eyes (in D) and the meridian(s) where it occurs.
- **Powers at that meridian**: OD and OS power there, and whether OD is more plus or more minus than OS.
- **Spherical equivalent difference** (OD − OS).
- **Chart**: signed difference (OD − OS) across every meridian from 0° to 180°, with the peak meridian(s) marked.

Special cases handled:

- If two meridians tie for the greatest difference, both are reported.
- If the difference is the same in every meridian (for example, identical cylinder and axis in both eyes), the result says so.
- An axis outside 0–180 prompts a correction instead of a result.

## How it works

The power of an eye in meridian *m* is

```
P(m) = S + C · sin²(m − axis)
```

The difference between the eyes can be rewritten with `sin²β = (1 − cos 2β) / 2` as

```
OD − OS = K + P·cos(2m) + Q·sin(2m)
```

which is a sinusoid with amplitude `R = √(P² + Q²)`. The signed difference is therefore greatest and smallest at meridians 90° apart, and the largest absolute difference is `max(|K + R|, |K − R|)`. Values are rounded to 0.01 D, and a meridian of 0° is reported as 180°.

## Notes

- All computation happens locally in the browser; nothing is sent anywhere.

## License

MIT. See [LICENSE](LICENSE).
