# Metamorphic testing of a sentiment model (small experiment)

*Goal:* check whether a sentiment model keeps its answer when a movie review is changed in a way that should not change its sentiment.

*Setup*
- Model: distilbert-base-uncased-finetuned-sst-2-english
- Data: 100 random Rotten Tomatoes validation reviews (seed 42)

*Changes tested*
- A neutral sentence added at the end
- A neutral sentence added at the start
- "movie" and "film" swapped (27 reviews contained one of these words)

*Results (label changed)*
- Neutral sentence at end: 1 of 100
- Neutral sentence at start: 1 of 100
- Movie/film swap: 1 of 27

*Findings*
- "a movie to forget" changed from NEGATIVE (0.99) to POSITIVE (0.78 with the sentence at the end, 0.64 at the start).
- One lower-confidence review (POSITIVE 0.79) changed after the movie/film swap.

*Limits:* one model, 100 reviews, simple changes. Only two different reviews changed, so no general conclusion can be drawn. Stronger changes (for example spelling errors or reordered sentences) are future work.
