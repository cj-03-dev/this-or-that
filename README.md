# This or That: Longevity Edition

**30 seconds for 3 years of life.**

Pick 2 foods and a goal, and get a clear verdict with the official data behind it. 1000 foods from India, South Asia, Europe and the world, every value taken from official food composition tables and checked against its source.

Live site: https://cj-03-dev.github.io/this-or-that/

## What it does

- Compares any 2 of 1000 foods for four goals: longevity, weight loss, protein, and before a workout
- Shows a clear winner, scores out of 100, and up to 3 plain reasons (for example "More fibre: 8.6 g vs 1.9 g")
- Shows every number per 100 g, where it came from, and how the score was built
- Search understands everyday Indian names such as palak, haldi and dahi
- Built to be simple for anyone: large text, clear buttons, minimal wording
- Stores nothing: no accounts, no cookies, no tracking

## The data

| Region | Foods |
| --- | --- |
| South Asia (including 200 from India) | 300 |
| Europe | 100 |
| Rest of the world | 600 |

| Source | Foods |
| --- | --- |
| Indian Food Composition Tables 2017 (IFCT), ICMR-National Institute of Nutrition | 230 |
| USDA National Nutrient Database for Standard Reference, Release 28 | 549 |
| McCance and Widdowson's Composition of Foods Integrated Dataset 2019 (CoFID), UK | 221 |

Every value, along with its source and source ID, is shown in the site itself under each comparison. The raw dataset export and the full verification workbook are kept outside this repository.

## How every value was verified

1. **Source re-read.** A separate program, written independently of the one that built the data, re-opened each original source file, found every food by its source ID, redid every unit conversion and compared all 19 nutrient fields. 19,000 checks, zero transcription errors.
2. **Sense checks.** Every food was tested for impossible or unusual values, such as energy above 900 kcal per 100 g, parts adding up to more than 100 g, sugar above total carbs, or fatty acids above total fat.
3. **Cross-database check.** Where the same food exists in another database, key values were compared and every large disagreement was investigated.

Results: 914 verified cleanly, 67 verified with an explanation, 12 corrected with a documented note, 7 kept with a source inconsistency noted.

Two corrections worth knowing about:

- The digital copy of IFCT used here lists ghee, vanaspati and nine cooking oils at 0 kcal. Energy was calculated from fat at 9 kcal per g.
- IFCT labels duck as "meat, with skin", but its values match skinless duck meat in USDA, so it is shown as lean duck meat.

## How the scores work

The longevity score (0 to 100) follows the logic of the Alternative Healthy Eating Index, the eating pattern most strongly linked to healthy ageing in a 30-year study of more than 105,000 people (Tessier et al., Nature Medicine, 2025).

- Each food starts from a base score for its food type (vegetables, legumes and fruit high; processed meat, sugary drinks and sweets low)
- Points are added for fibre, protein, long-chain omega-3, healthy fats and potassium
- Points are taken off for sugar, saturated fat, sodium and trans fat
- The maths is fixed: the same food always gets the same score, and every point is listed

The weight loss, protein and pre-workout scores reweight the same data for each goal.

## Ask about any food

The version hosted inside Claude also has a question box that answers only from the 1000 checked foods and cites each source code. It is not included in this GitHub copy.

## Limits

- Values are per 100 g as listed (mostly raw). Cooking changes them.
- IFCT often reports about twice the fibre of USDA and CoFID for the same food, because of method and edible-portion differences.
- 121 foods have no sugar value in their source. These are marked, not filled in.
- Some results may still look inconsistent. Work continues on the more complex factors behind healthy ageing, and on which biomarkers and nutrients matter most, so the scoring model will keep changing.
- General information only, not medical advice.

## Coming next

Personalised picks for age, gender and health conditions: high blood pressure, type 2 diabetes, PCOS, high cholesterol, fatty liver, and weight.

## Credits and licences

Developed by Chirag Joshi: https://www.linkedin.com/in/cj-ceo-vm/

Built with Claude (Anthropic) as the project for Anthropic's AI Fluency course. I set the scope, picked the foods, chose the scoring approach and the design direction, and signed off every decision. Claude did the building and the checking at speed.

- IFCT 2017 values: ICMR-National Institute of Nutrition, via the open `ifct2017` data package (AGPL-3.0)
- USDA SR28: public domain
- CoFID 2019: contains public sector information licensed under the Open Government Licence v3.0
- Fonts: Playfair Display and Lato. Globe coastlines: Natural Earth (public domain).

Independent, non-commercial personal project. Not affiliated with or endorsed by ICMR-NIN, the USDA or the UK government.
