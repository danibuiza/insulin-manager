# Insulin Calculator

A web-based insulin dose calculator for people with diabetes. Calculates bolus insulin based on carbohydrates, blood glucose levels, and various adjustment factors.

## Features

- **Multi-language support**: English, German, Spanish, Japanese, and Mandarin Chinese
- **Carbohydrate-based dosing**: Enter KE (Kohlenhydrateinheiten/Carbohydrate Units, 1 KE = 10g carbs)
- **Glucose correction**: Calculates correction dose based on current vs target blood glucose
- **Time-based factors**: Configure different correction factors, insulin factors, and targets for morning, midday, evening, and night
- **Fatty meal support**: Split dosing for fatty/very fatty meals (pizza, burgers, etc.)
- **Sport adjustment**: Reduce dose by 10-50% based on planned physical activity
- **Active insulin tracking**: Subtract insulin already taken in the last 3 hours
- **URL parameters**: Pre-fill values via URL for quick access
- **Persistent settings**: Time-based factors are saved to localStorage

## Formula

```
Insulin Dose = (KE × Factor) + ((Current Glucose - Target) / Correction Factor)
             × (1 - Sport Reduction)
             - Active Insulin
```

Result is rounded down to the nearest 0.5 units.

## Usage

### Basic Usage

1. Open `index.html` in a web browser
2. Enter your current blood glucose (mg/dl) and/or carbohydrate units (KE)
3. Click Calculate

### Configure Time-Based Factors

Click the ⚙️ settings toggle to set different values for each time period:
- **Morning** (6:00-10:59)
- **Midday** (11:00-16:59)
- **Evening** (17:00-20:59)
- **Night** (21:00-5:59)

Each time slot has:
- **Target**: Target blood glucose (mg/dl)
- **Correction**: mg/dl drop per 1 unit of insulin
- **Factor**: Units of insulin per KE

### Fatty Meals

For high-fat meals that cause delayed glucose spikes:
- **🥗 Normal**: Full dose at once
- **🍕 Fatty**: 60% now, 40% after 1-2 hours
- **🍔 Very Fatty**: 50% now, 50% after 1-2 hours

### Sport Adjustment

If exercising within the next 2 hours:
- **🚫 None**: No reduction
- **🚶 Light**: -10%
- **🏃 Moderate**: -25%
- **🏋️ Intense**: -50%

## URL Parameters

Pre-fill values by adding parameters to the URL:

| Parameter | Description | Values |
|-----------|-------------|--------|
| `glucose` | Current blood glucose | Number (mg/dl) |
| `ke` | Carbohydrate units | Number |
| `insulin` | Active insulin (last 3h) | Number |
| `sport` | Sport level | `none`, `light`, `moderate`, `intense` |
| `meal` | Meal type | `normal`, `fatty`, `very-fatty` |
| `lang` | Language | `en`, `de`, `es`, `ja`, `zh` |

### Examples

```
index.html?glucose=180&ke=3
index.html?glucose=150&ke=2&sport=moderate&meal=fatty
index.html?lang=de&glucose=200&ke=4
```

## Files

- `index.html` - Single-file web application (no dependencies)

## Disclaimer

⚠️ This calculator is for informational purposes only. Always consult your healthcare provider before adjusting insulin doses.

## License

MIT License
