# Paid-social competitive intelligence: skin resurfacing lasers (US, Meta Ad Library)

Run date: 2026-09-18. Active ads only, country = US. Every figure below traces to an ad_archive_id in the CSV or to a fetched URL.

## Headline card

```
THE HOOK EVERYONE IS RUNNING: direct_offer  (32.0% of 660 ads)
THE FORMAT EVERYONE IS RUNNING: offer_promo (42.7%)
WHO THEY ARE ALL WRITING FOR: product_aware   (55.9%)
THE INDICATION EVERYONE IS SELLING: laxity_tightening (39.7%)
ADS THAT BREAK THEIR PROMISE ON THE PAGE THEY LINK TO: 5.4%
  (17 of 314 ads whose landing page was fetched and judged; 166 ads used lead forms
   with no page; a further 13.4% drift, i.e. 42 ads land on a generic page that buries the promise)
```

## How to read this run

**Harvest.** 18 of the 20 keyword_unordered searches completed (each capped at 25 result pages, about 750 ads), yielding **7,341 raw active US ads**. The last two ("sun damage treatment", "skin texture treatment") returned zero results because Meta soft-blocked the Ad Library for this account/IP from about 09:00 UTC (every search, including the normal UI, returned "No ads match" for the rest of the run). The same block stopped the per-brand seed harvest (search_type=page for the 29 verified page ids), so seed coverage below comes from the keyword harvest only. **3,517 ads across 1,179 advertisers passed the category filter** (an ad must name a resurfacing modality or platform: CO2/erbium, fractional, Halo/BBL/Moxi, Fraxel, Clear + Brilliant, IPL/photofacial, RF microneedling and its platforms, picosecond, CoolPeel/Tetra/Helix/UltraClear, Sofwave, Thermage, Opus, etc.; hair removal, tattoo removal, skincare products, dental/gyn/veterinary lasers and equipment-for-sale ads are excluded). 119 practice-facing B2B ads (demo requests, "your practice", ROI) were excluded from the consumer sample and are listed in `b2b_excluded_ids.json`.

**Sample frame (typed set).** 1,038 ad_archive_ids were typed: every category-relevant ad from a seed advertiser (cap 40 per advertiser, top 15 by days x variants plus 25 random), 4 per advertiser with 5+ relevant ads (top 2 plus 2 random), 2 per advertiser with 3 to 4 ads, every remaining ad running 365+ days, then random fill. 40 typed ads were then dropped as off-category on inspection (laser-technician training schools, dental Solea CO2, HPV surgery, Korean/Vietnamese/Colombian clinics targeting US users). Identical creatives that Meta lists under separate ad ids (same page, text, headline, description, media type, CTA and destination) were merged, summing variant_count: **998 ad ids became 660 unique creatives across 328 advertisers**, which is the `ads_read` denominator everywhere below. The CSV keeps the merged ids in `duplicate_ad_ids`.

**Seed advertiser verification.** Page ids were confirmed through the Ad Library advertiser typeahead so that reseller and franchisee pages are not mistaken for the brand; Dermani Medspa and Sculpted MD run per-location pages (franchise structure), which are counted under the brand. Because the own-page harvest was blocked, a brand with 0 below means "no category ad surfaced in 18 keyword searches", not "no active ads"; I could not confirm zero active ads for any seed.

| seed brand | advertiser page id (verified via Ad Library typeahead) | raw ads surfaced by keyword harvest | category-relevant | unique creatives in typed sample |
|---|---|---:|---:|---:|
| LaserAway | 157163837672241 | 17 | 17 | 7 |
| Ideal Image | 114966474839 | 0 | 0 | 0 |
| Skin Laundry | 166192383533295 | 55 | 45 | 6 |
| SEV Laser | 200980483389166 | 1 | 0 | 0 |
| Ever/Body | 2503136276381485 | 0 | 0 | 0 |
| SkinSpirit | 239659982790186 | 2 | 0 | 0 |
| Dermani Medspa | 456443908198839 + 4 location pages | 1 | 1 | 1 |
| Sono Bello | 98269389167 | 0 | 0 | 0 |
| Sculpted MD | 1190301761025215 + 3 location pages | 0 | 0 | 0 |
| Sciton | 306756699392007 | 0 | 0 | 0 |
| Solta Medical (Fraxel) | 74159253855 | 4 | 2 | 2 |
| Solta Medical (Thermage) | 71593529371 | 0 | 0 | 0 |
| Solta Medical (Clear + Brilliant) | 310074065672251 | 3 | 3 | 3 |
| Cutera | 136211510079 | 0 | 0 | 0 |
| Candela Medical | 191930614187092 | 7 | 5 | 0 |
| Cynosure | 97658592421 | 0 | 0 | 0 |
| InMode | 165377763630843 (found in results; typeahead did not return it) | 18 | 18 | 3 |
| Lumenis | 353875395010336 / 107459272709756 / 254608784628337 | 0 | 0 | 0 |
| Sofwave | 102681937798972 | 379 | 368 | 18 |
| Alma Lasers | 836042789796646 | 0 | 0 | 0 |
| Venus Concept | 216809948376155 (page is named Venus Aesthetic Intelligence) | 29 | 29 | 1 |
| Aerolase | 312502441826 | 0 | 0 | 0 |

**Judgment method.** Literal fields (device_named, modality, price_disclosure, provider_signal, state-level geo, CTA mapping, advertiser_type for verified seeds) are rule-coded from the ad text with stated confidence; interpretive fields (hook, format, offer, cta_intent, awareness, driver, funnel, indication, downtime, proof, city geo, scores, claim_risk) were judged one pass per ad by a model against the fixed enums with per-field confidence and a runner-up value where one was weighed. Judgments are text-only: creative thumbnails in the Ad Library are tokenised, expiring CDN URLs, so the CSV carries each ad's permanent Ad Library link (`ad_library_url`) instead. proof_asset therefore reflects what the copy signals, not what the image shows. Two mappings to know: Sofwave (ultrasound) and Thermage (monopolar RF) sit outside the modality enum and are coded `unspecified` with device_platforms naming them; Halo is coded `hybrid_multiple` as a hybrid fractional platform.

**Landing pages.** 307 unique destination URLs among the typed ads; 260 were attempted (40 of the 300-page cap were held back for the seed-page harvest that never unblocked), 206 fetched and 54 failed (robots.txt disallow, timeouts, empty JS shells, 404). Each fetch captured the H1, subhead, visible offer, primary CTA and above-the-fold text; a second model pass judged messaging_match ad by ad. Nothing was inferred for a page that could not be fetched.


## 6a. Distribution tables (all ads read)

**hook_archetype**

| value | count | % |
|---|---:|---:|
| direct_offer | 211 | 32.0% |
| bold_claim | 123 | 18.6% |
| problem_callout | 93 | 14.1% |
| flat_spec | 91 | 13.8% |
| question | 52 | 7.9% |
| curiosity_tease | 39 | 5.9% |
| social_proof | 36 | 5.5% |
| before_after_reveal | 15 | 2.3% |

**format**

| value | count | % |
|---|---:|---:|
| offer_promo | 282 | 42.7% |
| problem_solution | 96 | 14.5% |
| catalog_generic | 52 | 7.9% |
| educational_howto | 52 | 7.9% |
| product_announcement | 46 | 7.0% |
| testimonial_ugc | 34 | 5.2% |
| provider_authority | 31 | 4.7% |
| comparison_switch | 25 | 3.8% |
| before_after_showcase | 22 | 3.3% |
| lifestyle_aspiration | 20 | 3.0% |

**offer**

| value | count | % |
|---|---:|---:|
| no_offer | 275 | 41.7% |
| dollar_off | 95 | 14.4% |
| percent_off | 87 | 13.2% |
| event_flash_sale | 59 | 8.9% |
| first_treatment_price | 50 | 7.6% |
| package_bundle | 37 | 5.6% |
| free_consult | 28 | 4.2% |
| gift_with_treatment | 24 | 3.6% |
| financing_monthly | 5 | 0.8% |

**cta_intent**

| value | count | % |
|---|---:|---:|
| lead_capture | 295 | 44.7% |
| learn_educate | 132 | 20.0% |
| book_appointment | 121 | 18.3% |
| message_us | 79 | 12.0% |
| free_consult | 21 | 3.2% |
| purchase_package | 7 | 1.1% |
| call_now | 5 | 0.8% |

**awareness_stage**

| value | count | % |
|---|---:|---:|
| product_aware | 369 | 55.9% |
| most_aware | 185 | 28.0% |
| solution_aware | 74 | 11.2% |
| unaware | 23 | 3.5% |
| problem_aware | 9 | 1.4% |

**driver**

| value | count | % |
|---|---:|---:|
| price_value | 285 | 43.2% |
| transformation | 195 | 29.5% |
| trust_safety | 69 | 10.5% |
| downtime_avoidance | 24 | 3.6% |
| lifestyle_aspiration | 24 | 3.6% |
| status_identity | 22 | 3.3% |
| social_proof | 20 | 3.0% |
| convenience_time | 11 | 1.7% |
| fear_loss | 10 | 1.5% |

**funnel**

| value | count | % |
|---|---:|---:|
| cold_prospecting | 299 | 45.3% |
| bottom_retargeting | 201 | 30.5% |
| mid_consideration | 160 | 24.2% |

**indication**

| value | count | % |
|---|---:|---:|
| laxity_tightening | 262 | 39.7% |
| unspecified | 100 | 15.2% |
| general_glow | 86 | 13.0% |
| fine_lines_wrinkles | 72 | 10.9% |
| pigmentation_sun_damage | 68 | 10.3% |
| texture_pores | 36 | 5.5% |
| acne_scarring | 32 | 4.8% |
| melasma | 2 | 0.3% |
| redness_rosacea | 2 | 0.3% |

**modality**

| value | count | % |
|---|---:|---:|
| rf_microneedling | 210 | 31.8% |
| unspecified | 137 | 20.8% |
| ablative_co2_erbium | 120 | 18.2% |
| hybrid_multiple | 118 | 17.9% |
| non_ablative_fractional | 66 | 10.0% |
| ipl_bbl | 7 | 1.1% |
| picosecond | 2 | 0.3% |

**downtime_handling**

| value | count | % |
|---|---:|---:|
| not_mentioned | 457 | 69.2% |
| downtime_minimized | 118 | 17.9% |
| downtime_denied | 69 | 10.5% |
| downtime_disclosed | 16 | 2.4% |

Supporting fields

**device_named**

| value | count | % |
|---|---:|---:|
| yes | 492 | 74.5% |
| no | 168 | 25.5% |

**proof_asset**

| value | count | % |
|---|---:|---:|
| none | 468 | 70.9% |
| stat_or_study | 87 | 13.2% |
| patient_testimonial | 55 | 8.3% |
| before_after_photo | 37 | 5.6% |
| provider_on_camera | 13 | 2.0% |

**price_disclosure**

| value | count | % |
|---|---:|---:|
| none | 411 | 62.3% |
| exact_price | 226 | 34.2% |
| from_price | 18 | 2.7% |
| monthly_payment | 5 | 0.8% |

**provider_signal**

| value | count | % |
|---|---:|---:|
| none | 600 | 90.9% |
| licensed_generic | 28 | 4.2% |
| md_supervised_claimed | 25 | 3.8% |
| board_certified_named | 7 | 1.1% |

**geo_signal**

| value | count | % |
|---|---:|---:|
| none | 326 | 49.4% |
| city_or_neighborhood_named | 311 | 47.1% |
| state_named | 23 | 3.5% |

**claim_risk**

| value | count | % |
|---|---:|---:|
| no | 267 | 40.5% |
| yes | 245 | 37.1% |
| unclear | 148 | 22.4% |

**messaging_match**

| value | count | % |
|---|---:|---:|
| holds | 255 | 38.6% |
| unclear | 180 | 27.3% |
| instant_form_no_page | 166 | 25.2% |
| drifts | 42 | 6.4% |
| breaks | 17 | 2.6% |

**media_type**

| value | count | % |
|---|---:|---:|
| video | 275 | 41.7% |
| image | 167 | 25.3% |
| carousel_image | 155 | 23.5% |
| carousel_video | 63 | 9.5% |

**advertiser_type**

| value | count | % |
|---|---:|---:|
| single_location | 600 | 90.9% |
| device_manufacturer | 36 | 5.5% |
| national_chain | 14 | 2.1% |
| regional_group | 10 | 1.5% |

## 6b. Split by advertiser type, and each type's biggest deviation from the category norm

### single_location (n = 600)

| field | top value | % of type | category % | deviation |
|---|---|---:|---:|---:|
| hook_archetype | direct_offer | 33.2% | 32.0% | +1.2pp |
| format | offer_promo | 44.7% | 42.7% | +2.0pp |
| offer | no_offer | 38.5% | 41.7% | -3.2pp |
| cta_intent | lead_capture | 46.5% | 44.7% | +1.8pp |
| awareness_stage | product_aware | 55.0% | 55.9% | -0.9pp |
| driver | price_value | 44.7% | 43.2% | +1.5pp |
| funnel | cold_prospecting | 43.5% | 45.3% | -1.8pp |
| indication | laxity_tightening | 40.8% | 39.7% | +1.1pp |
| modality | rf_microneedling | 33.8% | 31.8% | +2.0pp |
| downtime_handling | not_mentioned | 67.0% | 69.2% | -2.2pp |

Biggest deviation: **offer = no_offer** at 38.5% vs 41.7% category (-3.2pp).

### device_manufacturer (n = 36)

| field | top value | % of type | category % | deviation |
|---|---|---:|---:|---:|
| hook_archetype | social_proof | 36.1% | 5.5% | +30.6pp |
| format | testimonial_ugc | 30.6% | 5.2% | +25.4pp |
| offer | no_offer | 100.0% | 41.7% | +58.3pp |
| cta_intent | learn_educate | 58.3% | 20.0% | +38.3pp |
| awareness_stage | product_aware | 94.4% | 55.9% | +38.5pp |
| driver | transformation | 27.8% | 29.5% | -1.7pp |
| funnel | cold_prospecting | 66.7% | 45.3% | +21.4pp |
| indication | laxity_tightening | 38.9% | 39.7% | -0.8pp |
| modality | unspecified | 52.8% | 20.8% | +32.0pp |
| downtime_handling | not_mentioned | 86.1% | 69.2% | +16.9pp |

Biggest deviation: **offer = no_offer** at 100.0% vs 41.7% category (+58.3pp).

### national_chain (n = 14)

| field | top value | % of type | category % | deviation |
|---|---|---:|---:|---:|
| hook_archetype | direct_offer | 71.4% | 32.0% | +39.4pp |
| format | offer_promo | 78.6% | 42.7% | +35.9pp |
| offer | first_treatment_price | 64.3% | 7.6% | +56.7pp |
| cta_intent | learn_educate | 78.6% | 20.0% | +58.6pp |
| awareness_stage | most_aware | 57.1% | 28.0% | +29.1pp |
| driver | price_value | 85.7% | 43.2% | +42.5pp |
| funnel | bottom_retargeting | 57.1% | 30.5% | +26.6pp |
| indication | general_glow | 50.0% | 13.0% | +37.0pp |
| modality | unspecified | 57.1% | 20.8% | +36.3pp |
| downtime_handling | not_mentioned | 100.0% | 69.2% | +30.8pp |

Biggest deviation: **cta_intent = learn_educate** at 78.6% vs 20.0% category (+58.6pp).

### regional_group (n = 10)

| field | top value | % of type | category % | deviation |
|---|---|---:|---:|---:|
| hook_archetype | question | 30.0% | 7.9% | +22.1pp |
| format | catalog_generic | 30.0% | 7.9% | +22.1pp |
| offer | no_offer | 60.0% | 41.7% | +18.3pp |
| cta_intent | book_appointment | 40.0% | 18.3% | +21.7pp |
| awareness_stage | solution_aware | 50.0% | 11.2% | +38.8pp |
| driver | social_proof | 40.0% | 3.0% | +37.0pp |
| funnel | cold_prospecting | 80.0% | 45.3% | +34.7pp |
| indication | general_glow | 50.0% | 13.0% | +37.0pp |
| modality | unspecified | 70.0% | 20.8% | +49.2pp |
| downtime_handling | not_mentioned | 100.0% | 69.2% | +30.8pp |

Biggest deviation: **modality = unspecified** at 70.0% vs 20.8% category (+49.2pp).

## Per-advertiser table

Advertisers with 3 or more unique creatives in the sample (full list for all advertisers is in `advertiser_table.csv`). Mismatch rate = drifts + breaks as a share of that advertiser's landing pages actually fetched; blank where no page was fetched. Deviation = the single (field, value) where the advertiser most exceeds the category share.

| advertiser | type | ads | dominant hook | dominant format | dominant indication | dominant awareness | offer type | pages tested | mismatch % | claim risk % | biggest deviation | longest days |
|---|---|---:|---|---|---|---|---|---:|---:|---:|---|---:|
| Sofwave | device_manufacturer | 18 | social_proof (67%) | testimonial_ugc (33%) | laxity_tightening (67%) | product_aware (100%) | no_offer (100%) | 2 | 0 | 22 | modality=unspecified (100% vs +79pp) | 197 |
| LaserAway | national_chain | 7 | direct_offer (100%) | offer_promo (71%) | general_glow (43%) | most_aware (71%) | percent_off (43%) | 7 | 29 | 0 | funnel=bottom_retargeting (100% vs +70pp) | 31 |
| Skin Laundry | national_chain | 6 | bold_claim (50%) | offer_promo (83%) | general_glow (50%) | product_aware (50%) | first_treatment_price (100%) | 3 | 33 | 17 | offer=first_treatment_price (100% vs +92pp) | 24 |
| newskin | single_location | 4 | problem_callout (75%) | problem_solution (100%) | pigmentation_sun_damage (75%) | product_aware (100%) | gift_with_treatment (75%) | 4 | 0 | 25 | format=problem_solution (100% vs +86pp) | 16 |
| OmniSculptMD | single_location | 4 | direct_offer (75%) | before_after_showcase (50%) | general_glow (25%) | product_aware (75%) | dollar_off (75%) | 1 | 100 | 100 | offer=dollar_off (75% vs +61pp) | 1221 |
| Labelleviemedspa | single_location | 4 | bold_claim (50%) | testimonial_ugc (25%) | general_glow (50%) | product_aware (100%) | no_offer (100%) | 0 |  | 25 | cta_intent=learn_educate (100% vs +80pp) | 529 |
| Kyss Med Spa | single_location | 4 | flat_spec (25%) | problem_solution (50%) | general_glow (50%) | solution_aware (50%) | no_offer (50%) | 0 |  | 25 | cta_intent=message_us (100% vs +88pp) | 541 |
| Timeless Skin & Wellness | single_location | 4 | direct_offer (100%) | offer_promo (100%) | general_glow (50%) | most_aware (100%) | package_bundle (75%) | 0 |  | 0 | awareness_stage=most_aware (100% vs +72pp) | 14 |
| BHRC DFW | regional_group | 4 | question (75%) | catalog_generic (75%) | general_glow (75%) | solution_aware (100%) | no_offer (75%) | 3 | 100 | 0 | awareness_stage=solution_aware (100% vs +89pp) | 189 |
| Radiant Beauty & Health | single_location | 4 | flat_spec (75%) | comparison_switch (100%) | texture_pores (100%) | product_aware (75%) | no_offer (100%) | 4 | 0 | 0 | format=comparison_switch (100% vs +96pp) | 14 |
| South Coast MedSpa | single_location | 4 | problem_callout (50%) | before_after_showcase (50%) | acne_scarring (50%) | product_aware (100%) | no_offer (50%) | 0 |  | 25 | modality=ablative_co2_erbium (100% vs +82pp) | 155 |
| Paloma Clinic Spa | single_location | 4 | flat_spec (50%) | problem_solution (50%) | acne_scarring (50%) | solution_aware (100%) | free_consult (50%) | 0 |  | 0 | awareness_stage=solution_aware (100% vs +89pp) | 144 |
| Coastal Aesthetics | single_location | 4 | direct_offer (50%) | offer_promo (100%) | fine_lines_wrinkles (100%) | most_aware (100%) | dollar_off (75%) | 4 | 0 | 75 | indication=fine_lines_wrinkles (100% vs +89pp) | 74 |
| Venus Aesthetics Miami | device_manufacturer | 4 | flat_spec (50%) | before_after_showcase (50%) | general_glow (25%) | product_aware (50%) | no_offer (100%) | 0 |  | 0 | offer=no_offer (100% vs +58pp) | 154 |
| Marcos Medical Care & Wellness | single_location | 4 | question (50%) | problem_solution (50%) | pigmentation_sun_damage (50%) | product_aware (100%) | no_offer (100%) | 0 |  | 0 | modality=non_ablative_fractional (100% vs +90pp) | 99 |
| Kalon Aesthetics & Surgery | single_location | 4 | question (50%) | offer_promo (75%) | laxity_tightening (50%) | problem_aware (50%) | event_flash_sale (100%) | 4 | 0 | 0 | driver=lifestyle_aspiration (100% vs +96pp) | 17 |
| Studio-MD | single_location | 4 | flat_spec (50%) | provider_authority (50%) | laxity_tightening (100%) | product_aware (100%) | free_consult (50%) | 2 | 50 | 0 | driver=transformation (100% vs +70pp) | 88 |
| Dra. Eunice Magaña | single_location | 4 | bold_claim (50%) | educational_howto (75%) | laxity_tightening (75%) | product_aware (100%) | no_offer (100%) | 0 |  | 50 | cta_intent=message_us (100% vs +88pp) | 620 |
| SKYN Weight Loss + Wellness | single_location | 4 | flat_spec (50%) | catalog_generic (75%) | laxity_tightening (75%) | product_aware (100%) | no_offer (100%) | 0 |  | 0 | modality=rf_microneedling (100% vs +68pp) | 101 |
| Skinney Medspa | single_location | 4 | bold_claim (50%) | offer_promo (75%) | laxity_tightening (50%) | product_aware (50%) | gift_with_treatment (50%) | 0 |  | 50 | modality=unspecified (100% vs +79pp) | 117 |
| Aesthetics by Alyssa | single_location | 4 | direct_offer (75%) | comparison_switch (50%) | laxity_tightening (100%) | most_aware (75%) | dollar_off (50%) | 4 | 0 | 100 | modality=rf_microneedling (100% vs +68pp) | 108 |
| ProCare Wellness Institute | single_location | 4 | direct_offer (100%) | offer_promo (100%) | laxity_tightening (100%) | most_aware (100%) | package_bundle (100%) | 4 | 0 | 100 | offer=package_bundle (100% vs +94pp) | 81 |
| The Blessings Medical Clinic | single_location | 4 | flat_spec (75%) | catalog_generic (75%) | unspecified (100%) | product_aware (100%) | no_offer (100%) | 0 |  | 25 | cta_intent=message_us (100% vs +88pp) | 17 |
| Genesis Lifestyle Medicine - Texas | single_location | 4 | direct_offer (100%) | offer_promo (100%) | laxity_tightening (100%) | most_aware (100%) | dollar_off (100%) | 3 | 0 | 0 | offer=dollar_off (100% vs +86pp) | 37 |
| A Younger You Medical Spa | single_location | 4 | curiosity_tease (50%) | offer_promo (50%) | texture_pores (50%) | product_aware (50%) | package_bundle (50%) | 2 | 100 | 0 | cta_intent=book_appointment (75% vs +57pp) | 21 |
| Integrated Aesthetics | single_location | 4 | question (50%) | problem_solution (50%) | laxity_tightening (100%) | product_aware (100%) | no_offer (100%) | 3 | 0 | 75 | downtime_handling=downtime_denied (100% vs +90pp) | 132 |
| DermaTouch RN | single_location | 4 | direct_offer (100%) | offer_promo (100%) | laxity_tightening (100%) | most_aware (100%) | percent_off (100%) | 3 | 0 | 0 | offer=percent_off (100% vs +87pp) | 24 |
| TREAT Medspa | single_location | 4 | bold_claim (25%) | educational_howto (25%) | laxity_tightening (75%) | product_aware (100%) | percent_off (50%) | 2 | 50 | 75 | modality=unspecified (75% vs +54pp) | 14 |
| Elinea SF | single_location | 3 | flat_spec (67%) | provider_authority (67%) | unspecified (67%) | product_aware (33%) | no_offer (67%) | 0 |  | 0 | format=provider_authority (67% vs +62pp) | 203 |
| NEOSkin Promos | single_location | 3 | direct_offer (100%) | offer_promo (100%) | unspecified (67%) | most_aware (100%) | dollar_off (100%) | 3 | 67 | 0 | offer=dollar_off (100% vs +86pp) | 112 |
| Cool Springs Plastic Surgery | single_location | 3 | curiosity_tease (33%) | product_announcement (67%) | pigmentation_sun_damage (67%) | product_aware (67%) | no_offer (33%) | 2 | 0 | 0 | cta_intent=purchase_package (67% vs +66pp) | 28 |
| EDEN Plastic Surgery Miami | single_location | 3 | curiosity_tease (100%) | testimonial_ugc (100%) | laxity_tightening (100%) | product_aware (100%) | no_offer (100%) | 0 |  | 33 | format=testimonial_ugc (100% vs +95pp) | 211 |
| BodyLase Med Spa | regional_group | 3 | social_proof (67%) | provider_authority (67%) | unspecified (100%) | unaware (100%) | free_consult (67%) | 3 | 0 | 0 | awareness_stage=unaware (100% vs +96pp) | 126 |
| Carl Truesdale, M.D. | single_location | 3 | problem_callout (33%) | problem_solution (67%) | unspecified (100%) | product_aware (100%) | no_offer (100%) | 3 | 0 | 67 | driver=trust_safety (100% vs +90pp) | 107 |
| Sirens Med Spa | single_location | 3 | bold_claim (33%) | product_announcement (33%) | general_glow (100%) | product_aware (100%) | no_offer (67%) | 2 | 50 | 33 | indication=general_glow (100% vs +87pp) | 380 |
| LeVogue Med Spa | single_location | 3 | direct_offer (100%) | offer_promo (100%) | general_glow (33%) | most_aware (100%) | percent_off (100%) | 0 |  | 67 | offer=percent_off (100% vs +87pp) | 194 |
| NM Stem Cell & Wellness | single_location | 3 | curiosity_tease (100%) | offer_promo (100%) | laxity_tightening (100%) | product_aware (100%) | free_consult (100%) | 0 |  | 100 | cta_intent=free_consult (100% vs +97pp) | 81 |
| Dr. Chopra Plastic Surgery | single_location | 3 | before_after_reveal (67%) | before_after_showcase (67%) | laxity_tightening (67%) | product_aware (67%) | no_offer (100%) | 0 |  | 33 | funnel=mid_consideration (100% vs +76pp) | 109 |
| Cartessa Aesthetics | device_manufacturer | 3 | bold_claim (67%) | product_announcement (67%) | unspecified (100%) | product_aware (100%) | no_offer (100%) | 3 | 0 | 0 | indication=unspecified (100% vs +85pp) | 88 |
| Vanity Aesthetics Colorado Springs | single_location | 3 | problem_callout (100%) | problem_solution (100%) | acne_scarring (100%) | product_aware (100%) | no_offer (100%) | 0 |  | 0 | indication=acne_scarring (100% vs +95pp) | 52 |
| Dr. Paul Jarrod Frank | single_location | 3 | bold_claim (100%) | educational_howto (100%) | general_glow (100%) | product_aware (67%) | no_offer (100%) | 1 | 100 | 33 | format=educational_howto (100% vs +92pp) | 4 |
| FACE Skincare~Medical~Wellness | single_location | 3 | bold_claim (100%) | product_announcement (100%) | general_glow (67%) | product_aware (100%) | gift_with_treatment (67%) | 0 |  | 33 | format=product_announcement (100% vs +93pp) | 11 |
| Luna Dermatology | single_location | 3 | question (100%) | offer_promo (100%) | general_glow (100%) | most_aware (100%) | first_treatment_price (100%) | 3 | 0 | 100 | offer=first_treatment_price (100% vs +92pp) | 87 |
| xTool | single_location | 3 | curiosity_tease (67%) | testimonial_ugc (67%) | unspecified (100%) | product_aware (100%) | no_offer (100%) | 3 | 0 | 0 | indication=unspecified (100% vs +85pp) | 42 |
| Norse Organics | single_location | 3 | curiosity_tease (100%) | comparison_switch (100%) | acne_scarring (100%) | problem_aware (67%) | no_offer (100%) | 3 | 0 | 100 | driver=fear_loss (100% vs +98pp) | 64 |
| Solta Medical (Clear + Brilliant) | device_manufacturer | 3 | curiosity_tease (67%) | testimonial_ugc (100%) | general_glow (100%) | product_aware (100%) | no_offer (100%) | 3 | 0 | 0 | format=testimonial_ugc (100% vs +95pp) | 80 |
| InMode | device_manufacturer | 3 | flat_spec (33%) | comparison_switch (33%) | acne_scarring (33%) | product_aware (100%) | no_offer (100%) | 1 | 0 | 0 | offer=no_offer (100% vs +58pp) | 114 |
| Just Wellness | single_location | 3 | flat_spec (33%) | educational_howto (33%) | pigmentation_sun_damage (67%) | product_aware (100%) | no_offer (67%) | 0 |  | 0 | indication=pigmentation_sun_damage (67% vs +56pp) | 10 |
| Skin Plus Beauty | single_location | 3 | flat_spec (67%) | offer_promo (67%) | pigmentation_sun_damage (33%) | product_aware (100%) | dollar_off (33%) | 3 | 33 | 33 | downtime_handling=downtime_minimized (100% vs +82pp) | 80 |
| Serenity Aesthetics & Wellness | single_location | 3 | direct_offer (100%) | offer_promo (100%) | general_glow (100%) | most_aware (100%) | dollar_off (100%) | 3 | 0 | 0 | indication=general_glow (100% vs +87pp) | 73 |
| Lauréate Aesthetics | single_location | 3 | bold_claim (67%) | educational_howto (67%) | laxity_tightening (67%) | product_aware (100%) | free_consult (67%) | 0 |  | 100 | funnel=mid_consideration (100% vs +76pp) | 289 |
| SkinLab by Maffi Plastic Surgery | single_location | 3 | direct_offer (100%) | offer_promo (100%) | pigmentation_sun_damage (100%) | most_aware (100%) | dollar_off (100%) | 0 |  | 0 | indication=pigmentation_sun_damage (100% vs +90pp) | 2 |
| Skin Deep Medical Spa- Steven Bloch MD | single_location | 3 | flat_spec (67%) | lifestyle_aspiration (67%) | general_glow (67%) | product_aware (100%) | no_offer (100%) | 0 |  | 0 | format=lifestyle_aspiration (67% vs +64pp) | 360 |
| Texas Neuro Eye & Plastic Surgery | single_location | 3 | problem_callout (100%) | offer_promo (100%) | laxity_tightening (100%) | product_aware (100%) | percent_off (100%) | 0 |  | 0 | offer=percent_off (100% vs +87pp) | 109 |
| Ageless Center | single_location | 3 | bold_claim (100%) | offer_promo (100%) | laxity_tightening (100%) | product_aware (100%) | percent_off (100%) | 3 | 0 | 100 | offer=percent_off (100% vs +87pp) | 64 |
| SER Aesthetics | single_location | 3 | direct_offer (67%) | offer_promo (100%) | laxity_tightening (100%) | most_aware (100%) | gift_with_treatment (100%) | 1 | 0 | 100 | offer=gift_with_treatment (100% vs +96pp) | 66 |
| Self Aesthetics & Wellness | single_location | 3 | direct_offer (100%) | offer_promo (100%) | laxity_tightening (100%) | most_aware (100%) | dollar_off (67%) | 3 | 0 | 100 | awareness_stage=most_aware (100% vs +72pp) | 32 |
| Green Leaf Medi Spa | single_location | 3 | problem_callout (67%) | offer_promo (100%) | laxity_tightening (67%) | product_aware (67%) | event_flash_sale (100%) | 3 | 100 | 67 | offer=event_flash_sale (100% vs +91pp) | 15 |
| Radiant Lab Medical Aesthetics | single_location | 3 | social_proof (100%) | offer_promo (100%) | laxity_tightening (100%) | most_aware (100%) | first_treatment_price (100%) | 3 | 0 | 0 | hook_archetype=social_proof (100% vs +94pp) | 30 |
| The Hughes Center for Aesthetic Medicine | single_location | 3 | direct_offer (100%) | offer_promo (100%) | fine_lines_wrinkles (100%) | most_aware (100%) | gift_with_treatment (100%) | 0 |  | 100 | offer=gift_with_treatment (100% vs +96pp) | 4 |
| Cleo Skin And Laser | single_location | 3 | problem_callout (67%) | problem_solution (67%) | acne_scarring (67%) | product_aware (67%) | no_offer (67%) | 3 | 67 | 67 | cta_intent=book_appointment (100% vs +82pp) | 32 |

## 6c. The 20 longest-running ads (days_running x variant_count)

variant_count = Meta's collation count summed across identical creatives that Meta lists under separate ad IDs (those IDs are in the CSV column `duplicate_ad_ids`).

**1. Sofwave** (device_manufacturer), ad_archive_id 1904080990214482, 193 days x 84 variants = 16212. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1904080990214482
   Headline: (none)  |  Opener: 🌊 Dr. Jenny Doyle, UK-based Oculoplastic Surgeon, explains how Sofwave™ helps improve skin laxity without surgery.  By stimulating your body’s natural collagen,
   `{"hook_archetype": "flat_spec", "format": "educational_howto", "offer": "no_offer", "cta_intent": "lead_capture", "awareness_stage": "product_aware", "driver": "trust_safety", "funnel": "cold_prospecting", "indication": "laxity_tightening", "device_named": "yes", "modality": "unspecified", "downtime_handling": "not_mentioned", "proof_asset": "provider_on_camera", "price_disclosure": "none", "provider_signal": "md_supervised_claimed", "geo_signal": "none", "hook_specificity": 2, "offer_strength": 0, "durability": 3, "claim_risk": "no", "messaging_match": "instant_form_no_page"}`

**2. Sofwave** (device_manufacturer), ad_archive_id 965755216321911, 137 days x 63 variants = 8631. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=965755216321911
   Headline: (none)  |  Opener: 🏆 This is what real patient says about Sofwave. “It made me feel like myself again.” Not just visible results - but a renewed sense of confidence.  A difference
   `{"hook_archetype": "social_proof", "format": "testimonial_ugc", "offer": "no_offer", "cta_intent": "lead_capture", "awareness_stage": "product_aware", "driver": "social_proof", "funnel": "cold_prospecting", "indication": "unspecified", "device_named": "yes", "modality": "unspecified", "downtime_handling": "not_mentioned", "proof_asset": "patient_testimonial", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "none", "hook_specificity": 1, "offer_strength": 0, "durability": 3, "claim_risk": "unclear", "messaging_match": "instant_form_no_page"}`

**3. Aria Integrative Health** (single_location), ad_archive_id 27068008219499410, 112 days x 45 variants = 5040. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=27068008219499410
   Headline: Experience EXION™ RF. Experience The Results!  |  Opener: Finally... a Microneedling procedure that's Proven + Cleared by the FDA... "EXION™ RF" is a MUST SEE! 💪
   `{"hook_archetype": "bold_claim", "format": "product_announcement", "offer": "no_offer", "cta_intent": "learn_educate", "awareness_stage": "product_aware", "driver": "trust_safety", "funnel": "cold_prospecting", "indication": "unspecified", "device_named": "yes", "modality": "rf_microneedling", "downtime_handling": "not_mentioned", "proof_asset": "stat_or_study", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "none", "hook_specificity": 1, "offer_strength": 0, "durability": 3, "claim_risk": "unclear", "messaging_match": "holds"}`

**4. HAUS Salon** (single_location), ad_archive_id 2195469214266070, 390 days x 12 variants = 4680. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=2195469214266070
   Headline: (none)  |  Opener: New Skin, Who This? ✨ Say hello to brighter, smoother, clearer skin. Our latest skin treatments — BBL + Moxi — are officially here at HAUS! Whether you’re targe
   `{"hook_archetype": "curiosity_tease", "format": "product_announcement", "offer": "no_offer", "cta_intent": "book_appointment", "awareness_stage": "product_aware", "driver": "transformation", "funnel": "cold_prospecting", "indication": "pigmentation_sun_damage", "device_named": "yes", "modality": "hybrid_multiple", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "none", "hook_specificity": 0, "offer_strength": 0, "durability": 3, "claim_risk": "unclear", "messaging_match": "unclear"}`

**5. Daela Cosmetic Tattoo** (single_location), ad_archive_id 965980545965677, 179 days x 20 variants = 3580. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=965980545965677
   Headline: {{product.name}}  |  Opener: {{product.brand}}
   `{"hook_archetype": "bold_claim", "format": "catalog_generic", "offer": "no_offer", "cta_intent": "book_appointment", "awareness_stage": "product_aware", "driver": "transformation", "funnel": "cold_prospecting", "indication": "general_glow", "device_named": "no", "modality": "unspecified", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "none", "hook_specificity": 0, "offer_strength": 0, "durability": 3, "claim_risk": "yes", "messaging_match": "holds"}`

**6. Skin Laundry** (national_chain), ad_archive_id 2301933473974537, 15 days x 210 variants = 3150. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=2301933473974537
   Headline: First Laser Facial $50 ($275 Value)  |  Opener: We take the guesswork out of skincare. At Skin Laundry, we tackle acne, redness and more with laser precision.
   `{"hook_archetype": "direct_offer", "format": "offer_promo", "offer": "first_treatment_price", "cta_intent": "learn_educate", "awareness_stage": "most_aware", "driver": "price_value", "funnel": "cold_prospecting", "indication": "redness_rosacea", "device_named": "no", "modality": "unspecified", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "exact_price", "provider_signal": "none", "geo_signal": "none", "hook_specificity": 1, "offer_strength": 2, "durability": 2, "claim_risk": "unclear", "messaging_match": "holds"}`

**7. Clique Salon and Med Spa** (single_location), ad_archive_id 367917582209176, 1492 days x 2 variants = 2984. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=367917582209176
   Headline: Clique Salon And Med Spa  |  Opener: Welcome to our business servicing the Lakeland & surrounding areas. Offering services such as Haircuts, Blow Outs, Conditioning treatments, Balayage and Special
   `{"hook_archetype": "flat_spec", "format": "catalog_generic", "offer": "no_offer", "cta_intent": "message_us", "awareness_stage": "product_aware", "driver": "lifestyle_aspiration", "funnel": "cold_prospecting", "indication": "unspecified", "device_named": "yes", "modality": "hybrid_multiple", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "city_or_neighborhood_named", "hook_specificity": 0, "offer_strength": 0, "durability": 3, "claim_risk": "no", "messaging_match": "instant_form_no_page"}`

**8. Premier Aesthetics of Billings Plastic Surgery** (single_location), ad_archive_id 1195798188345836, 695 days x 4 variants = 2780. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1195798188345836
   Headline: Schedule Your Consultation  |  Opener: Tim Loudan has been working with Premier Aesthetics of Yellowstone Plastic Surgery for many years, and PA is the only provider in the state of Montana to offer 
   `{"hook_archetype": "social_proof", "format": "testimonial_ugc", "offer": "no_offer", "cta_intent": "book_appointment", "awareness_stage": "product_aware", "driver": "downtime_avoidance", "funnel": "mid_consideration", "indication": "unspecified", "device_named": "yes", "modality": "unspecified", "downtime_handling": "downtime_denied", "proof_asset": "patient_testimonial", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "state_named", "hook_specificity": 1, "offer_strength": 0, "durability": 3, "claim_risk": "yes", "messaging_match": "drifts"}`

**9. JAX Aesthetics & Wellness Center** (single_location), ad_archive_id 1022107180792535, 51 days x 54 variants = 2754. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1022107180792535
   Headline: 50% OFF Voucher + Free Consult  |  Opener: 🚨 Hey, Women of Jacksonville & Surrounding Areas! 🚨 Want to reverse signs of aging and get glowing skin—without the needles or downtime?  Let’s be real. Who has
   `{"hook_archetype": "direct_offer", "format": "offer_promo", "offer": "percent_off", "cta_intent": "lead_capture", "awareness_stage": "product_aware", "driver": "price_value", "funnel": "cold_prospecting", "indication": "fine_lines_wrinkles", "device_named": "yes", "modality": "rf_microneedling", "downtime_handling": "downtime_denied", "proof_asset": "stat_or_study", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "city_or_neighborhood_named", "hook_specificity": 0, "offer_strength": 3, "durability": 1, "claim_risk": "yes", "messaging_match": "holds"}`

**10. HAUS Salon** (single_location), ad_archive_id 1460579364984850, 390 days x 7 variants = 2730. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1460579364984850
   Headline: BBL & Moxi Now at HAUS ✨ Book Today  |  Opener: New Skin, Who This? ✨ Say hello to brighter, smoother, clearer skin. Our latest skin treatments — BBL + Moxi — are officially here at HAUS! Whether you’re targe
   `{"hook_archetype": "flat_spec", "format": "product_announcement", "offer": "no_offer", "cta_intent": "book_appointment", "awareness_stage": "product_aware", "driver": "transformation", "funnel": "cold_prospecting", "indication": "pigmentation_sun_damage", "device_named": "yes", "modality": "hybrid_multiple", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "none", "hook_specificity": 1, "offer_strength": 0, "durability": 3, "claim_risk": "unclear", "messaging_match": "unclear"}`

**11. Sofwave** (device_manufacturer), ad_archive_id 1669575441153480, 197 days x 13 variants = 2561. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1669575441153480
   Headline: (none)  |  Opener: Confidence looks good on everyone.  🌊 Sofwave™ is trusted by experts worldwide to lift and refresh your skin, while keeping your natural volume intact.  Backed 
   `{"hook_archetype": "social_proof", "format": "lifestyle_aspiration", "offer": "no_offer", "cta_intent": "lead_capture", "awareness_stage": "product_aware", "driver": "trust_safety", "funnel": "cold_prospecting", "indication": "laxity_tightening", "device_named": "yes", "modality": "unspecified", "downtime_handling": "not_mentioned", "proof_asset": "stat_or_study", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "none", "hook_specificity": 0, "offer_strength": 0, "durability": 3, "claim_risk": "unclear", "messaging_match": "instant_form_no_page"}`

**12. Aesthetics by Vive** (single_location), ad_archive_id 1589863252705590, 65 days x 33 variants = 2145. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1589863252705590
   Headline: 50% OFF Morpheus8 RF + Free Skin Consult  |  Opener: 🚨 Bradenton women 35+ who want firmer, smoother, glowing skin without surgery or injectables… Most “miracle” creams barely move the needle. If you’re ready for 
   `{"hook_archetype": "direct_offer", "format": "offer_promo", "offer": "percent_off", "cta_intent": "lead_capture", "awareness_stage": "product_aware", "driver": "price_value", "funnel": "cold_prospecting", "indication": "laxity_tightening", "device_named": "yes", "modality": "rf_microneedling", "downtime_handling": "downtime_minimized", "proof_asset": "stat_or_study", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "city_or_neighborhood_named", "hook_specificity": 1, "offer_strength": 3, "durability": 1, "claim_risk": "unclear", "messaging_match": "holds"}`

**13. Aesthetics by VIP** (single_location), ad_archive_id 1611403900325687, 41 days x 49 variants = 2009. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1611403900325687
   Headline: 50% OFF Voucher + Free Skin Consult  |  Opener: 🚨 Hey, Women of Pinehurst & Surrounding Areas! Want to reverse signs of aging and get glowing skin—without the needles or downtime?  Let’s be real. Who has time
   `{"hook_archetype": "direct_offer", "format": "offer_promo", "offer": "percent_off", "cta_intent": "lead_capture", "awareness_stage": "product_aware", "driver": "price_value", "funnel": "cold_prospecting", "indication": "fine_lines_wrinkles", "device_named": "yes", "modality": "rf_microneedling", "downtime_handling": "downtime_denied", "proof_asset": "stat_or_study", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "city_or_neighborhood_named", "hook_specificity": 0, "offer_strength": 3, "durability": 1, "claim_risk": "yes", "messaging_match": "holds"}`

**14. 713 Wellness , Aesthetics and Medical Center** (single_location), ad_archive_id 888800180584659, 208 days x 8 variants = 1664. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=888800180584659
   Headline: ⚡ Agenda tu sesión de Láser CO2.  |  Opener: 😓¿𝗖𝗶𝗰𝗮𝘁𝗿𝗶𝗰𝗲𝘀, 𝗺𝗮𝗻𝗰𝗵𝗮𝘀 𝗼 𝗮𝗿𝗿𝘂𝗴𝗮𝘀 𝗽𝗿𝗼𝗳𝘂𝗻𝗱𝗮𝘀? Renueva tu piel con Láser CO₂  En 𝟳𝟭𝟯 W𝗲𝗹𝗹𝗻𝗲𝘀𝘀, 𝗔𝗲𝘀𝘁𝗵𝗲𝘁𝗶𝗰𝘀 𝗮𝗻𝗱 𝗠𝗲𝗱𝗶𝗰𝗮𝗹 𝗖𝗲𝗻𝘁𝗲𝗿  tenemos la solución que estabas espera
   `{"hook_archetype": "problem_callout", "format": "problem_solution", "offer": "no_offer", "cta_intent": "message_us", "awareness_stage": "solution_aware", "driver": "transformation", "funnel": "cold_prospecting", "indication": "fine_lines_wrinkles", "device_named": "no", "modality": "ablative_co2_erbium", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "none", "hook_specificity": 2, "offer_strength": 0, "durability": 3, "claim_risk": "yes", "messaging_match": "instant_form_no_page"}`

**15. Innova Beauty Clinic** (single_location), ad_archive_id 1510650869971045, 310 days x 5 variants = 1550. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1510650869971045
   Headline: (none)  |  Opener: ✨ ¡Rejuvenece tu piel con Morpheus 8! ✨  Morpheus 8 trabaja en las capas profundas de tu piel para reducir la flacidez y mejorar la tensión facial, dejando un r
   `{"hook_archetype": "flat_spec", "format": "problem_solution", "offer": "no_offer", "cta_intent": "message_us", "awareness_stage": "product_aware", "driver": "transformation", "funnel": "cold_prospecting", "indication": "laxity_tightening", "device_named": "yes", "modality": "rf_microneedling", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "none", "hook_specificity": 1, "offer_strength": 0, "durability": 3, "claim_risk": "no", "messaging_match": "unclear"}`

**16. Sirens Med Spa** (single_location), ad_archive_id 1108790770757521, 380 days x 4 variants = 1520. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1108790770757521
   Headline: (none)  |  Opener: That post-MOXI glow is real. ✨ Meet MOXI, the laser treatment everyone’s talking about.  It brightens, smooths, and gives your skin that fresh, even tone… all i
   `{"hook_archetype": "bold_claim", "format": "product_announcement", "offer": "no_offer", "cta_intent": "message_us", "awareness_stage": "product_aware", "driver": "downtime_avoidance", "funnel": "cold_prospecting", "indication": "general_glow", "device_named": "yes", "modality": "non_ablative_fractional", "downtime_handling": "downtime_denied", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "city_or_neighborhood_named", "hook_specificity": 1, "offer_strength": 0, "durability": 3, "claim_risk": "yes", "messaging_match": "instant_form_no_page"}`

**17. BHRC DFW** (regional_group), ad_archive_id 2220046521858200, 189 days x 8 variants = 1512. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=2220046521858200
   Headline: Book Now. Glow Later.  |  Opener: What does transformation look like for you?  Maybe it’s smoother, more even-toned skin. Maybe it’s a sculpted silhouette or feeling confident in your natural fe
   `{"hook_archetype": "question", "format": "catalog_generic", "offer": "no_offer", "cta_intent": "book_appointment", "awareness_stage": "solution_aware", "driver": "transformation", "funnel": "cold_prospecting", "indication": "general_glow", "device_named": "no", "modality": "unspecified", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "licensed_generic", "geo_signal": "city_or_neighborhood_named", "hook_specificity": 0, "offer_strength": 0, "durability": 3, "claim_risk": "no", "messaging_match": "unclear"}`

**18. BHRC DFW** (regional_group), ad_archive_id 1268478254645566, 185 days x 8 variants = 1480. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1268478254645566
   Headline: Book Now. Glow Later.  |  Opener: What does transformation look like for you?  Maybe it’s smoother, more even-toned skin. Maybe it’s a sculpted silhouette or feeling confident in your natural fe
   `{"hook_archetype": "question", "format": "catalog_generic", "offer": "no_offer", "cta_intent": "book_appointment", "awareness_stage": "solution_aware", "driver": "transformation", "funnel": "cold_prospecting", "indication": "general_glow", "device_named": "no", "modality": "unspecified", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "licensed_generic", "geo_signal": "city_or_neighborhood_named", "hook_specificity": 0, "offer_strength": 0, "durability": 3, "claim_risk": "no", "messaging_match": "drifts"}`

**19. BHRC DFW** (regional_group), ad_archive_id 1670170851005996, 183 days x 8 variants = 1464. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1670170851005996
   Headline: Book Now. Glow Later.  |  Opener: What does transformation look like for you?  Maybe it’s smoother, more even-toned skin. Maybe it’s a sculpted silhouette or feeling confident in your natural fe
   `{"hook_archetype": "question", "format": "catalog_generic", "offer": "no_offer", "cta_intent": "book_appointment", "awareness_stage": "solution_aware", "driver": "transformation", "funnel": "cold_prospecting", "indication": "general_glow", "device_named": "no", "modality": "unspecified", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "licensed_generic", "geo_signal": "city_or_neighborhood_named", "hook_specificity": 0, "offer_strength": 0, "durability": 3, "claim_risk": "no", "messaging_match": "drifts"}`

**20. Skin Deep Medical Spa- Steven Bloch MD** (single_location), ad_archive_id 1091985529586737, 360 days x 4 variants = 1440. https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&media_type=all&id=1091985529586737
   Headline: Reveal Your Best Skin with Fraxel® Laser  |  Opener: Transform your skin with the power of Fraxel Laser® - the cutting-edge treatment that rejuvenates your complexion, reduces imperfections, and brings out your na
   `{"hook_archetype": "bold_claim", "format": "lifestyle_aspiration", "offer": "no_offer", "cta_intent": "lead_capture", "awareness_stage": "product_aware", "driver": "transformation", "funnel": "cold_prospecting", "indication": "general_glow", "device_named": "yes", "modality": "non_ablative_fractional", "downtime_handling": "not_mentioned", "proof_asset": "none", "price_disclosure": "none", "provider_signal": "none", "geo_signal": "city_or_neighborhood_named", "hook_specificity": 1, "offer_strength": 0, "durability": 3, "claim_risk": "unclear", "messaging_match": "instant_form_no_page"}`

## 6d. Whitespace: indication x hook x awareness combinations under 5% of ads

117 distinct combinations appear in the data out of 360 possible (9 indications x 8 hooks x 5 stages). The category is concentrated: the top combination alone is 11.8% of ads. Combinations that are fully uncontested (0 ads) and marketing-relevant are listed first; the full grid with counts is in `whitespace_grid.csv`.

Top 10 crowded combinations (what NOT to copy without a twist):

| indication | hook | awareness | ads | % |
|---|---|---|---:|---:|
| laxity_tightening | direct_offer | most_aware | 78 | 11.8% |
| laxity_tightening | bold_claim | product_aware | 38 | 5.8% |
| general_glow | direct_offer | most_aware | 23 | 3.5% |
| fine_lines_wrinkles | direct_offer | most_aware | 22 | 3.3% |
| laxity_tightening | direct_offer | product_aware | 22 | 3.3% |
| laxity_tightening | problem_callout | product_aware | 21 | 3.2% |
| laxity_tightening | flat_spec | product_aware | 20 | 3.0% |
| unspecified | flat_spec | product_aware | 18 | 2.7% |
| unspecified | direct_offer | most_aware | 18 | 2.7% |
| laxity_tightening | question | product_aware | 17 | 2.6% |

Uncontested (0 ads) combinations on the indications a CO2 practice can own:

| indication | hook | awareness |
|---|---|---|
| acne_scarring | bold_claim | problem_aware |
| acne_scarring | problem_callout | problem_aware |
| acne_scarring | question | problem_aware |
| acne_scarring | question | solution_aware |
| acne_scarring | social_proof | problem_aware |
| acne_scarring | curiosity_tease | solution_aware |
| acne_scarring | before_after_reveal | problem_aware |
| acne_scarring | before_after_reveal | solution_aware |
| fine_lines_wrinkles | problem_callout | problem_aware |
| fine_lines_wrinkles | question | problem_aware |
| fine_lines_wrinkles | social_proof | problem_aware |
| fine_lines_wrinkles | social_proof | solution_aware |
| fine_lines_wrinkles | curiosity_tease | problem_aware |
| fine_lines_wrinkles | curiosity_tease | solution_aware |
| fine_lines_wrinkles | before_after_reveal | problem_aware |
| fine_lines_wrinkles | before_after_reveal | solution_aware |
| pigmentation_sun_damage | bold_claim | problem_aware |
| pigmentation_sun_damage | question | problem_aware |
| pigmentation_sun_damage | question | solution_aware |
| pigmentation_sun_damage | social_proof | problem_aware |
| pigmentation_sun_damage | social_proof | solution_aware |
| pigmentation_sun_damage | curiosity_tease | problem_aware |
| pigmentation_sun_damage | before_after_reveal | problem_aware |
| pigmentation_sun_damage | before_after_reveal | solution_aware |
| melasma | bold_claim | problem_aware |
| melasma | bold_claim | solution_aware |
| melasma | problem_callout | problem_aware |
| melasma | problem_callout | solution_aware |
| melasma | question | problem_aware |
| melasma | question | solution_aware |
| melasma | social_proof | problem_aware |
| melasma | social_proof | solution_aware |
| melasma | curiosity_tease | problem_aware |
| melasma | curiosity_tease | solution_aware |
| melasma | before_after_reveal | problem_aware |
| melasma | before_after_reveal | solution_aware |
| texture_pores | bold_claim | problem_aware |
| texture_pores | problem_callout | problem_aware |
| texture_pores | question | problem_aware |
| texture_pores | social_proof | problem_aware |
| texture_pores | social_proof | solution_aware |
| texture_pores | curiosity_tease | problem_aware |
| texture_pores | curiosity_tease | solution_aware |
| texture_pores | before_after_reveal | problem_aware |
| texture_pores | before_after_reveal | solution_aware |

Thinly contested (>0 but <2% of ads) on the same indications:

| indication | hook | awareness | ads | % |
|---|---|---|---:|---:|
| acne_scarring | bold_claim | solution_aware | 1 | 0.15% |
| acne_scarring | bold_claim | product_aware | 3 | 0.45% |
| acne_scarring | bold_claim | most_aware | 1 | 0.15% |
| acne_scarring | problem_callout | solution_aware | 6 | 0.91% |
| acne_scarring | problem_callout | product_aware | 13 | 1.97% |
| acne_scarring | flat_spec | solution_aware | 1 | 0.15% |
| acne_scarring | flat_spec | product_aware | 3 | 0.45% |
| acne_scarring | social_proof | solution_aware | 1 | 0.15% |
| acne_scarring | curiosity_tease | problem_aware | 2 | 0.3% |
| acne_scarring | curiosity_tease | product_aware | 1 | 0.15% |
| fine_lines_wrinkles | bold_claim | problem_aware | 1 | 0.15% |
| fine_lines_wrinkles | bold_claim | solution_aware | 2 | 0.3% |
| fine_lines_wrinkles | bold_claim | product_aware | 5 | 0.76% |
| fine_lines_wrinkles | problem_callout | solution_aware | 8 | 1.21% |
| fine_lines_wrinkles | problem_callout | product_aware | 10 | 1.52% |
| fine_lines_wrinkles | problem_callout | most_aware | 3 | 0.45% |
| fine_lines_wrinkles | question | unaware | 1 | 0.15% |
| fine_lines_wrinkles | question | solution_aware | 1 | 0.15% |
| fine_lines_wrinkles | question | product_aware | 3 | 0.45% |
| fine_lines_wrinkles | direct_offer | solution_aware | 2 | 0.3% |
| fine_lines_wrinkles | direct_offer | product_aware | 8 | 1.21% |
| fine_lines_wrinkles | flat_spec | solution_aware | 2 | 0.3% |
| fine_lines_wrinkles | flat_spec | product_aware | 3 | 0.45% |
| fine_lines_wrinkles | curiosity_tease | product_aware | 1 | 0.15% |
| pigmentation_sun_damage | bold_claim | solution_aware | 2 | 0.3% |
| pigmentation_sun_damage | bold_claim | product_aware | 13 | 1.97% |
| pigmentation_sun_damage | bold_claim | most_aware | 2 | 0.3% |
| pigmentation_sun_damage | problem_callout | problem_aware | 1 | 0.15% |
| pigmentation_sun_damage | problem_callout | solution_aware | 3 | 0.45% |
| pigmentation_sun_damage | problem_callout | product_aware | 9 | 1.36% |
| pigmentation_sun_damage | question | product_aware | 5 | 0.76% |
| pigmentation_sun_damage | direct_offer | product_aware | 7 | 1.06% |
| pigmentation_sun_damage | direct_offer | most_aware | 11 | 1.67% |
| pigmentation_sun_damage | flat_spec | product_aware | 7 | 1.06% |
| pigmentation_sun_damage | social_proof | product_aware | 2 | 0.3% |
| pigmentation_sun_damage | curiosity_tease | solution_aware | 1 | 0.15% |
| pigmentation_sun_damage | curiosity_tease | product_aware | 4 | 0.61% |
| pigmentation_sun_damage | before_after_reveal | product_aware | 1 | 0.15% |
| melasma | bold_claim | product_aware | 1 | 0.15% |
| melasma | flat_spec | product_aware | 1 | 0.15% |
| texture_pores | bold_claim | solution_aware | 3 | 0.45% |
| texture_pores | bold_claim | product_aware | 7 | 1.06% |
| texture_pores | problem_callout | solution_aware | 1 | 0.15% |
| texture_pores | problem_callout | product_aware | 1 | 0.15% |
| texture_pores | question | solution_aware | 2 | 0.3% |
| texture_pores | question | product_aware | 1 | 0.15% |
| texture_pores | direct_offer | product_aware | 5 | 0.76% |
| texture_pores | direct_offer | most_aware | 4 | 0.61% |
| texture_pores | flat_spec | solution_aware | 1 | 0.15% |
| texture_pores | flat_spec | product_aware | 7 | 1.06% |
| texture_pores | curiosity_tease | product_aware | 3 | 0.45% |
| texture_pores | before_after_reveal | product_aware | 1 | 0.15% |

## 6e. Landing page truth test

- Landing pages fetched and readable: **206** of 260 unique destination URLs attempted (cap 300). Pages that failed: **54** (robots.txt disallow, timeouts, empty shells, 404; listed in `landing_pages.csv`). Ads pointing at unfetched or failed pages are recorded as `unclear`, never guessed.
- Ads whose page was fetched and judged: 314. holds 255, drifts 42 (13.4%), **breaks 17 (5.4%)**.
- Instant-form ads with no page to test: **166** (25.2% of all ads read), reported separately.
- Ads marked unclear (page failed or beyond cap): 180.

Every `breaks` verdict:

| ad_archive_id | advertiser | why it breaks |
|---|---|---|
| 38063894589922335 | Fort Wayne Dermatology + Plastic Surgery & Aesthetics | ad sells Halo laser; page is CoolSculpting fat-reduction page, Halo absent |
| 970939461955879 | OmniSculptMD | ad $100 new-patient Helix CO2; page $100 off Botox/filler or $700 spend, Helix/CO2 absent |
| 1454863845966748 | Rejuvenations Lehigh Valley | ad Tetra PRO CoolPeel; generic homepage never names CoolPeel or CO2 |
| 794503373705933 | BHRC DFW | ad $100 off light CO2 resurfacing; location page has no CO2, shows member 30% off lasers instead |
| 1484499313022896 | Glo Esthetics Med Spa | ad's 'two MOXI included with RF Microneedling' offer absent everywhere; page is generic homepage, RF MN/MOXI only in deep list |
| 708174842219486 | Clinical Care 365 | ad over 50% off Morpheus8 + free consult, page is generic homepage with only free consultation; 50% off absent, Morpheus 8 only in service list |
| 1609755710669231 | Green Leaf Medi Spa | ad RF Microneedling with Exosomes $169 (reg $425), page is bare booking contact form; price absent everywhere, treatment only in service dropdown |
| 1072776101903454 | Green Leaf Medi Spa | ad RF Microneedling with Exosomes $169 (reg $425), page is bare booking contact form; price absent everywhere, treatment only in service dropdown |
| 1059280043376585 | Green Leaf Medi Spa | ad RF Microneedling with Exosomes fall offer $169 (reg $425), page is bare booking contact form; price absent everywhere, treatment only in service dropdown |
| 1394748376100934 | A Younger You Medical Spa | ad Darwin RF Microneedling series of 3 for $1,575 ($675 savings), page is generic homepage with free consultation; offer absent everywhere, RF microneedling not named |
| 1572822617770675 | A Younger You Medical Spa | ad Darwin RF Microneedling series of 3 for $1,575 ($675 savings), page is generic homepage with free consultation; offer absent everywhere, RF microneedling not named |
| 2094885121117919 | Fab Medical Aesthetics & Permanent Makeup | ad $297 RF microneedling facelift package; page sells Total Immune Boost IV $125, RF microneedling absent |
| 1090087833465903 | Fab Medical Aesthetics & Permanent Makeup | ad $297 RF microneedling facelift package; page sells Total Immune Boost IV $125, RF microneedling absent |
| 1066195829370906 | TREAT Medspa | ad code HANNAH 30% off first Sofwave; page homepage shows New Client 20% Off, Sofwave only in menu |
| 4431237127132429 | Inbloom Medical Spa Londonderry | ad is about Sofwave treatment; page is generic new-patient voucher form naming only CoolSculpting, Sofwave absent |
| 1081173118174364 | Inbloom Medical Spa Londonderry | ad is about Sofwave treatment; page is generic new-patient voucher form naming only CoolSculpting, Sofwave absent |
| 1591804232653380 | Skin Laundry | ad first Laser Facial $50; page is empty checkout view showing $75 Laundry Club price, no $50 offer |

## 6f. Claim risk

- claim_risk = yes: **37.1%** of ads read; unclear (thin or templated text, hedged borderline language): 22.4%.
- By advertiser type (yes rate): single_location 40.0%, device_manufacturer 11.1%, national_chain 7.1%, regional_group 0.0%.
- Pattern frequency among flagged ads (an ad can carry several): results/B&A without disclaimer 170, safety / no-downtime absolutes 64, medical outcome claim by non-physician 59, surgery/injectable comparison 51, erase/remove/eliminate 39, unsupported stat / FDA / study claim 31, reverse aging / years younger 31, permanence 14, guarantee 7.

## 6g. Offer landscape

- 41.7% of ads carry no offer at all. Among ads with an offer, the repeating structures are dollar-off (14.4%), percent-off (13.2%), a priced first treatment (7.6%) and time-boxed events (8.9%). Financing is almost absent (0.8%).
- Percent-off depths that repeat (depth: ads): 10% off: 6, 15% off: 9, 20% off: 20, 25% off: 4, 30% off: 33, 40% off: 24, 50% off: 61, 65% off: 6. 50% off is the modal discount, 30% and 40% next.
- Dollar-off amounts that repeat ($ off: ads): $25: 2, $50: 2, $100: 6, $150: 4, $200: 10, $250: 13, $300: 13, $475: 2, $500: 12, $550: 2, $750: 8, $895: 2, $1000: 2. $200 to $300 off a single session and $500 to $750 off a package are the two clusters.
- Disclosed prices: 194 ads state a treatment price. Median disclosed price **$348**, quartiles $249 / $347 / $500.
- Median disclosed price by modality: rf_microneedling $499 (n=67), ablative_co2_erbium $297 (n=40), unspecified $299 (n=32), hybrid_multiple $274 (n=28), non_ablative_fractional $299 (n=23), ipl_bbl $237 (n=4).
- Monthly payments are stated in only 6 ads (values: $57, $57, $57, $57, $250, $500); median $57/mo, too few to generalise.
- Package structures that repeat: free add-on with purchase (37), bundle/combo (12), financing (8), series/package of N (6), buy X get Y (4), gift card (3), membership (1).

## 6h. Device concentration

Spend signal = sum of days_running x variant_count over ads that name the platform. Indications are what the ads claim for that device.

| platform | ads naming it | advertisers | spend signal | median days | top indications claimed |
|---|---:|---:|---:|---:|---|
| sofwave | 84 | 36 | 40782 | 29.0 | laxity_tightening (62), unspecified (16), fine_lines_wrinkles (5) |
| morpheus8 | 166 | 95 | 30740 | 44.5 | laxity_tightening (127), unspecified (11), fine_lines_wrinkles (10) |
| moxi | 70 | 38 | 15643 | 50.0 | pigmentation_sun_damage (29), general_glow (19), fine_lines_wrinkles (8) |
| bbl | 48 | 29 | 13309 | 40.0 | pigmentation_sun_damage (25), general_glow (13), laxity_tightening (4) |
| exion | 16 | 11 | 12626 | 27.5 | unspecified (6), fine_lines_wrinkles (5), laxity_tightening (4) |
| coolpeel | 44 | 30 | 9120 | 64.0 | fine_lines_wrinkles (12), texture_pores (12), laxity_tightening (6) |
| deka | 17 | 10 | 3156 | 74 | fine_lines_wrinkles (4), laxity_tightening (3), general_glow (3) |
| lumecca | 2 | 2 | 3018 | 754.5 | unspecified (2) |
| ultraclear | 15 | 7 | 2829 | 107 | laxity_tightening (5), general_glow (4), unspecified (4) |
| halo | 19 | 12 | 2783 | 17 | pigmentation_sun_damage (8), unspecified (4), fine_lines_wrinkles (4) |
| inmode | 9 | 6 | 2733 | 114 | unspecified (4), laxity_tightening (2), general_glow (2) |
| fraxel | 12 | 8 | 2356 | 44.0 | general_glow (4), acne_scarring (4), pigmentation_sun_damage (3) |
| potenza | 19 | 13 | 2014 | 15 | laxity_tightening (13), unspecified (3), texture_pores (1) |
| opus | 14 | 8 | 1863 | 75.5 | laxity_tightening (5), fine_lines_wrinkles (5), general_glow (2) |
| sciton | 16 | 11 | 1064 | 15.5 | pigmentation_sun_damage (6), unspecified (5), general_glow (3) |
| co2re | 3 | 3 | 1030 | 144 | unspecified (2), general_glow (1) |
| picosure | 6 | 5 | 989 | 4.5 | laxity_tightening (2), pigmentation_sun_damage (2), unspecified (1) |
| clear+brilliant | 9 | 4 | 730 | 36 | general_glow (5), texture_pores (2), unspecified (2) |
| venus | 4 | 1 | 616 | 154.0 | general_glow (1), pigmentation_sun_damage (1), laxity_tightening (1) |
| tixel | 2 | 2 | 592 | 74.5 | texture_pores (1), pigmentation_sun_damage (1) |
| vivace | 4 | 3 | 564 | 18.5 | texture_pores (2), unspecified (2) |
| aerolase | 3 | 1 | 417 | 99 | unspecified (2), general_glow (1) |

## Steal list: 10 angles to test

Each angle is written as indication + hook_archetype + format + awareness_stage + offer, with a sample headline, a primary-text opener, and the evidence it rests on. Copy is original and hedged; nothing below reproduces a competitor's claim language (see the compliance note for what to avoid).

1. **acne_scarring + problem_callout + problem_solution + solution_aware + no_offer**
   Headline: "Acne scars are a depth problem, not a skincare problem"
   Opener: "If creams and peels have not changed the texture of your scars, that is because scarring sits below where topicals reach. Fractional CO2 works at that depth. Here is what a treatment plan looks like."
   Why: uncontested whitespace. acne_scarring x problem_callout x solution_aware is 6 ads (0.9%) and every problem-aware acne-scar combination is 0 ads (6d). The nearest proven neighbour, problem_callout x solution_aware across all indications, runs a median 76 days vs 31 for direct_offer ads (6c).

2. **pigmentation_sun_damage + before_after_reveal + before_after_showcase + solution_aware + no_offer**
   Headline: "Twelve weeks after one fractional CO2 session (individual results vary)"
   Opener: "Same patient, same lighting, no filter. This is what sun damage looked like before and after a single Helix CO2 pass; healing took eight days. Results vary and a consultation decides candidacy."
   Why: before_after_showcase is the longest-lived format in the set (median 118 days, n=22) yet before_after_reveal is only 2.3% of hooks, and pigmentation x before_after_reveal x solution_aware is 0 ads (6d). Disclaimer in the creative keeps it out of the claim-risk bucket that 174 competitor ads fell into.

3. **texture_pores + question + educational_howto + solution_aware + no_offer**
   Headline: "Why do pores look bigger every year?"
   Opener: "Pores do not grow, the collagen around them loosens. A resurfacing laser rebuilds that support. Two minutes on how it works and who it is for."
   Why: educational_howto runs a median 94 days (n=52) vs 31 for offer_promo, and texture_pores x question x solution_aware is 2 ads (0.3%) (6d).

4. **fine_lines_wrinkles + problem_callout + comparison_switch + solution_aware + free_consult**
   Headline: "Filler smooths the line. Resurfacing changes the skin around it."
   Opener: "If you have been topping up injectables for years and the etched lines keep coming back, that is a skin-quality problem. A fractional CO2 plan is a different lever, not a replacement. Book a consult to see if it fits."
   Why: comparison_switch is 3.8% of formats and fine_lines x problem_callout x solution_aware is 8 ads (1.2%). free_consult offers run a median 93 days vs 16 for event sales (6c). Keep the comparison factual; 51 flagged competitor ads used surgery/injectable comparisons as superiority claims.

5. **pigmentation_sun_damage + flat_spec + provider_authority + product_aware + no_offer**
   Headline: "Helix CO2 resurfacing, performed under physician direction in [city]"
   Opener: "[Provider name, credential] explains how she sets Helix CO2 depth for sun damage, what the first week looks like, and who she turns away."
   Why: provider_authority is 4.7% of formats but runs a median 88 days (n=31); provider_signal = none on 91% of ads, so a named, credentialed provider is nearly uncontested. Device names carry attention (72% of ads name one), so keep the platform in the headline.

6. **texture_pores + bold_claim + problem_solution + product_aware + dollar_off, with downtime disclosed**
   Headline: "Smoother texture, tighter-looking pores, about 5 days of social downtime"
   Opener: "Most laser ads will not tell you what recovery looks like. Ours: red on day one, flaking by day three, makeup by day five. $[X] off a single Helix CO2 session this month."
   Why: downtime_disclosed is 2.4% of ads while downtime_denied plus minimized is 28%; the honest version is whitespace and avoids the 66 no-downtime absolutes flagged for risk. PURE Medical Spa Idaho's disclosed-downtime CoolPeel ad (1038211768783076) is the format's proof point at 74 days x 9 variants with a landing page that holds.

7. **laxity_tightening + problem_callout + comparison_switch + solution_aware + no_offer**
   Headline: "Researching Morpheus8? Read this before you book a series."
   Opener: "RF microneedling and fractional CO2 both build collagen. They differ in what they do to the surface, how many sessions you need and what a week after looks like. Here is the side by side."
   Why: laxity_tightening is the most crowded indication (40% of ads) but 53% of it is direct_offer or bold_claim at product/most_aware and almost none of it educates; problem_callout x solution_aware on laxity is 2 ads (0.3%) (6d). Morpheus8 carries the second largest spend signal (166 ads, 95 advertisers), so intercepting its research traffic is cheap reach.

8. **acne_scarring + social_proof + testimonial_ugc + product_aware + first_treatment_price**
   Headline: "'I stopped wearing foundation to the gym.' A Helix CO2 patient, 3 months on"
   Opener: "[First name] had ice-pick scarring from her twenties. Two Helix sessions later she talks about what changed and what did not. First session $[X] for new patients; results vary."
   Why: acne_scarring x social_proof is 1 ad in the set at solution_aware and 0 at problem_aware (6d); testimonial_ugc runs a median 80 days vs 31 for offer_promo. first_treatment_price is the national chains' playbook (9 of 14 chain creatives) and their pages mostly hold (7 of 10 fetched).

9. **general_glow + direct_offer + offer_promo + most_aware + first_treatment_price, geo-named**
   Headline: "[Neighbourhood]: first Helix CO2 session $[X], this month"
   Opener: "[Neighbourhood] and [neighbouring town] readers: your first fractional CO2 resurfacing session is $[X] for new patients through [date]. Consultation included. Limited appointments each week."
   Why: this is the category's proven bottom-funnel unit (laxity/glow x direct_offer x most_aware is 15% of all ads and the top combination), so run it for retargeting only. Median disclosed price for ablative CO2 is $297 (n=40); set the intro price against that and keep the landing page identical to the ad, since 5.4% of fetched pages break and 13.4% drift, and 36 of the 59 mismatches carry an offer the page does not repeat (no-offer creatives drift too: 23 of 82 fetched, usually to a generic homepage).

10. **melasma + question + educational_howto + problem_aware + free_consult**
    Headline: "Is it melasma or sun damage? The answer changes the treatment."
    Opener: "Brown patches that darken every summer and fade in winter behave differently from sun spots, and the wrong laser can make them worse. A physician assessment tells them apart. Free skin consult."
    Why: melasma is 0.3% of ads (2 of 660) and every melasma x hook x awareness combination is under 1% (6d). Frame as assessment, not treatment promise: melasma is a medical diagnosis and 62 competitor ads were flagged for medical outcome claims by non-physician advertisers.

Two structural notes from 6c that apply to all ten: no_offer creatives outlive offer creatives (median 81 vs 31 days), and city-named creatives churn faster than un-geo'd ones (median 37 vs 53 days), so the evergreen angles above (1 to 5, 7) should carry the always-on budget and the offer angles (6, 8, 9) should be rotated.

## Compliance note: claim patterns competitors are running that we should not copy

37.1% of ads read carry at least one claim pattern that would not survive an FTC, state medical board or Meta health-claims review, and a further 22.4% are unclear (templated or thin text). Single-location med spas are the offenders (40.0% yes) while national chains (7.1%) and manufacturers (11.1%) are largely clean. Every flagged ad_archive_id is in `review_queue.csv` (field = claim_risk) and the CSV column `claim_risk_reason` quotes the phrase. The patterns, most frequent first:

1. **Results and before/after language with no "results vary" disclaimer** (174 flagged ads). Competitors post transformation reveals and "look at these results" with nothing qualifying them. Rule for us: every result image or result sentence carries "individual results vary" in the creative, not only on the page.
2. **Absolutes about safety and downtime** (66). "No downtime", "zero downtime", "painless", "no side effects", "safe for all skin types", including on ablative CO2, which has real downtime. Rule: state the expected recovery in days; never say none.
3. **Medical outcome claims by non-physician advertisers** (62). Med spas claiming to treat melasma, rosacea, or to "reverse" damage, sometimes with a nurse or aesthetician as the only provider. Rule: outcome language only for indications on the device's clearance, and provider credential visible when a medical outcome is implied.
4. **Surgery and injectable superiority claims** (51). "Non-surgical facelift", "facelift results without surgery", "better than Botox". Rule: compare mechanisms, never outcomes, and never use the word facelift for an energy device.
5. **Erase / remove / eliminate / goodbye-to language** (41) and **permanence** (14). "Erase dark spots", "remove wrinkles", "say goodbye to acne scars for good", "permanent results". Rule: reduce, improve, soften; never erase or permanent.
6. **Unsupported statistics and FDA wording** (31). "FDA-approved" for devices that are FDA-cleared; "reverses up to 5 years of structural damage"; "the #1 CO2 treatment"; "gold standard" with no source. Rule: "FDA-cleared" only, and any number must cite the study or be dropped.
7. **Years-younger and reverse-aging** (31). "Look 10 years younger", "turn back the clock a decade". Rule: do not quantify age reversal.
8. **Guarantees** (7). "Guaranteed results", "money-back if you do not see a difference". Rule: never.

Two adjacent risks the data shows: 25% of ads are instant-form lead ads that collect health-adjacent data with no page-level disclosure, and 5.4% of fetched landing pages contradict the ad's price or treatment, which is an advertising-substantiation problem as well as a conversion one. Keep the ad's price, device and indication on the page above the fold.

Advertisers with a 100% claim-risk rate on 3 or more unique creatives in the sample (do not benchmark against these): OmniSculptMD, Aesthetics by Alyssa, ProCare Wellness Institute, NM Stem Cell & Wellness, Luna Dermatology, Norse Organics, Lauréate Aesthetics, Ageless Center, SER Aesthetics, Self Aesthetics & Wellness, The Hughes Center for Aesthetic Medicine (full rates per advertiser in `advertiser_table.csv`).

## Needs-a-human queue

1888 items in `review_queue.csv`: 1495 judgments with confidence under 0.50 or a runner-up within 0.10, plus 393 claim_risk = yes/unclear flags (every one is queued because the category is regulated). By field: claim_risk 506, funnel 244, driver 212, format 199, indication 193, hook_archetype 155, offer 121, awareness_stage 92, cta_intent 77, proof_asset 63, downtime_handling 17, geo_signal 9.

First 25 low-confidence or tied judgments:

| ad_archive_id | advertiser | field | candidates | conf | why |
|---|---|---|---|---:|---|
| 2066986240529900 | Elinea SF | funnel | mid_consideration / cold_prospecting | 0.5 | runner-up cold_prospecting at 0.4 |
| 2109186649904911 | Elinea SF | funnel | bottom_retargeting / cold_prospecting | 0.5 | runner-up cold_prospecting at 0.4 |
| 2109186649904911 | Elinea SF | claim_risk | unclear / no | 0.5 | runner-up no at 0.4 |
| 988309210402149 | Elinea SF | hook_archetype | flat_spec / bold_claim | 0.5 | runner-up bold_claim at 0.4 |
| 1338955208117654 | Antiage Institute: Medical Spa & Wellness Center | funnel | bottom_retargeting / cold_prospecting | 0.5 | runner-up cold_prospecting at 0.45 |
| 1338955208117654 | Antiage Institute: Medical Spa & Wellness Center | indication | fine_lines_wrinkles / general_glow | 0.45 | confidence 0.45; runner-up general_glow at 0.4 |
| 1338955208117654 | Antiage Institute: Medical Spa & Wellness Center | proof_asset | stat_or_study / none | 0.5 | runner-up none at 0.45 |
| 1022158343587747 | Antiage Institute: Medical Spa & Wellness Center | funnel | bottom_retargeting / cold_prospecting | 0.5 | runner-up cold_prospecting at 0.45 |
| 1022158343587747 | Antiage Institute: Medical Spa & Wellness Center | indication | fine_lines_wrinkles / general_glow | 0.45 | confidence 0.45; runner-up general_glow at 0.4 |
| 1022158343587747 | Antiage Institute: Medical Spa & Wellness Center | proof_asset | stat_or_study / none | 0.5 | runner-up none at 0.45 |
| 986797950753916 | NEOSkin Promos | funnel | bottom_retargeting / cold_prospecting | 0.5 | runner-up cold_prospecting at 0.4 |
| 995970023179592 | NEOSkin Promos | funnel | bottom_retargeting / cold_prospecting | 0.5 | runner-up cold_prospecting at 0.4 |
| 995970023179592 | NEOSkin Promos | proof_asset | stat_or_study / none | 0.5 | runner-up none at 0.45 |
| 2287191362113701 | NEOSkin Promos | funnel | bottom_retargeting / cold_prospecting | 0.5 | runner-up cold_prospecting at 0.4 |
| 2287191362113701 | NEOSkin Promos | proof_asset | stat_or_study / none | 0.5 | runner-up none at 0.45 |
| 1035526536132954 | Cool Springs Plastic Surgery | driver | status_identity / transformation | 0.45 | confidence 0.45; runner-up transformation at 0.4 |
| 1035526536132954 | Cool Springs Plastic Surgery | funnel | cold_prospecting / mid_consideration | 0.5 | runner-up mid_consideration at 0.4 |
| 1035526536132954 | Cool Springs Plastic Surgery | indication | pigmentation_sun_damage / texture_pores | 0.5 | runner-up texture_pores at 0.4 |
| 1086883191049528 | Cool Springs Plastic Surgery | driver | price_value / fear_loss | 0.45 | confidence 0.45 |
| 1086883191049528 | Cool Springs Plastic Surgery | indication | pigmentation_sun_damage / texture_pores | 0.5 | runner-up texture_pores at 0.45 |
| 3361352980730861 | OVME | claim_risk | unclear / no | 0.5 | runner-up no at 0.45 |
| 2110488083013563 | OVME | claim_risk | unclear / no | 0.5 | runner-up no at 0.45 |
| 1299803948894850 | MidAmerica Medical Spa | format | problem_solution / lifestyle_aspiration | 0.45 | confidence 0.45 |
| 1299803948894850 | MidAmerica Medical Spa | indication | general_glow / texture_pores | 0.4 | confidence 0.4; runner-up texture_pores at 0.35 |
| 2405464579939937 | MidAmerica Medical Spa | hook_archetype | problem_callout / flat_spec | 0.45 | confidence 0.45 |

## Run stamp

- ads_read: **660** unique creatives (from 1038 ad_archive_ids typed; 7341 raw active US ads harvested; 3517 passed the category filter across 1179 advertisers)
- advertisers: **328**
- total judgments: **14520** typed fields (660 ads x 22 enum/score fields) plus 314 messaging_match verdicts
- pages_fetched: **206** (pages_failed 54, instant_form_count 166)
- elapsed: about 2 h 05 min wall clock (harvest 08:20 to 09:00 UTC, judgment and landing pages 09:10 to 10:20 UTC, Ad Library blocked from 09:00 UTC onward)
- keyword searches run: 18 of 20 completed: skin resurfacing, laser resurfacing, CO2 laser, fractional laser, Halo laser, BBL Hero, Moxi laser, Fraxel, Clear + Brilliant, Morpheus8, RF microneedling, Potenza, Sofwave, CoolPeel, Opus Plasma, laser facial, acne scar treatment, melasma treatment; blocked: sun damage treatment, skin texture treatment; seed brands verified: see scope note


## Addendum (2026-09-18, later the same day): creative visuals and dashboard

The text-only caveat above is now partly lifted. Using a logged-out Ad Library session, the server-rendered result pages were fetched for every seed page and for keyword searches built from each ad's own copy, and the first creative of each ad was downloaded and reduced to a 480px JPEG. **588 of 660 unique creatives (89.1%) now have a stored thumbnail** (`competitive-intel/thumbs/<ad_archive_id>.jpg`), every one classified against a fixed visual enum by a model looking at the image only (no copy shown). 72 creatives have no thumbnail: 25 are catalog/DCO template ads whose image is pulled from a product feed and is not exposed in the Ad Library render, and 47 could not be surfaced in any render within the request budget (the Ad Library soft-blocked the logged-out session twice; the deeper LaserAway, Sofwave, TREAT Medspa and Integrated Aesthetics libraries account for most of them). The CSV now carries `thumbnail_file` plus the eleven `visual_*` columns; `visual_type = no_thumbnail` marks the gap explicitly.

**Dashboard.** `competitive-intel/index.html` is a self-contained page in the "steal the whole category" layout: KPI strip, filterable thumbnail grid of all 660 creatives (image ads show the downloaded image; video ads show the poster frame with a play badge), a per-ad teardown with every typed field, its confidence bar and the runner-up value in orange when the call was close, the category distribution columns, and the needs-a-human cards. Every card links to the ad's permanent Ad Library page (country=US). Open it from the folder; it needs the `thumbs/` folder beside it.

**What the creatives show (n = 588 thumbnails).**

visual_type

| value | count | % |
|---|---:|---:|
| treatment_in_progress | 158 | 26.9% |
| before_after | 98 | 16.7% |
| text_graphic_offer | 71 | 12.1% |
| lifestyle_model | 57 | 9.7% |
| provider_on_camera | 56 | 9.5% |
| device_product_shot | 30 | 5.1% |
| other | 22 | 3.7% |
| patient_result_closeup | 21 | 3.6% |
| patient_testimonial | 20 | 3.4% |
| ugc_selfie | 18 | 3.1% |
| clinic_interior_team | 16 | 2.7% |
| illustration_infographic | 11 | 1.9% |

production

| value | count | % |
|---|---:|---:|
| template_graphic | 251 | 42.7% |
| clinic_real | 210 | 35.7% |
| polished_studio | 61 | 10.4% |
| ugc_phone | 61 | 10.4% |

text_overlay

| value | count | % |
|---|---:|---:|
| heavy | 289 | 49.1% |
| light | 169 | 28.7% |
| none | 125 | 21.3% |

palette

| value | count | % |
|---|---:|---:|
| white_clean | 183 | 31.1% |
| warm_skin_tones | 124 | 21.1% |
| dark_moody | 109 | 18.5% |
| mixed | 80 | 13.6% |
| pastel_soft | 46 | 7.8% |
| brand_color_block | 41 | 7.0% |

Supporting: price visibly rendered on the creative 28.1% (165); a platform name or logo visible on the creative 38.3% (225); a skin close-up fills the frame 25.3%; one person in frame 65.3%, no people 15.6%; a visible results disclaimer on only 2.7% (16) of creatives.

By advertiser type (top three visual types):

| type | thumbs | top visual types |
|---|---:|---|
| single_location | 544 | treatment_in_progress 28%, before_after 18%, text_graphic_offer 12% |
| regional_group | 9 | text_graphic_offer 56%, patient_testimonial 33%, treatment_in_progress 11% |
| device_manufacturer | 29 | device_product_shot 24%, patient_testimonial 14%, treatment_in_progress 14% |
| national_chain | 6 | treatment_in_progress 33%, logo_brand_only 17%, lifestyle_model 17% |

**Three things the images add to the text read.**

1. Before/after is far bigger on the image than in the copy. The copy-based `proof_asset = before_after_photo` was 5.6% of ads; the image says 16.7% of creatives are before/after splits and another 3.6% are result close-ups. Of the 98 before/after creatives, 5 carry a visible "results vary" line. 82 ads coded `proof_asset = none` from their copy actually show a before/after or result close-up, so the compliance exposure in 6f is understated, not overstated.
2. Price on the creative is a separate lever from price in the copy: 46 of the 165 creatives with a rendered price have `price_disclosure = none` in the ad text, i.e. the offer lives in the image only. Filter the dashboard by visual type `text_graphic_offer` to see the whole templated-offer wall; template graphics are 42.7% of all creatives.
3. `treatment_in_progress` (handpiece on skin, gloves, goggles) is the modal image at 26.9%, mostly clinic-shot video stills, while `provider_on_camera` is 9.5% and `ugc_selfie` 3.1%. Steal-list angles 5 (named provider) and 8 (patient UGC) therefore sit in visual whitespace as well as copy whitespace; angle 2 (disclaimed before/after) competes with a crowded image type and wins only on the disclaimer and the honest framing.

Visual judgments are single-pass model reads of a 480px thumbnail (first image or video poster frame only; carousel cards beyond the first are not seen), with a confidence per ad in `visual_confidence`. Treat them as directional; the review queue does not include them.
