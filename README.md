# Stats work on self-reported Arknights tags

[/u/patrickpeng168][reddit-user] has taken the effort to organize a large dataset
for tag recruitment. I've decided to see how independent each tag is to one other.

The dataset was taken from [this reddit post][reddit], and entires are from
2/23/2020 11:07:01 to 3/2/2020 20:50:41.

_A quick lesson on stats: Two events are independent if they don't influence
the probability of each other, like with two separate coin flips. In contrast,
two events are dependent on each other if they somehow skew each other's
probability, such as rain on a day if it's cloudy or sunny. In our case, we want
to find out if tags are independent or not, which then lets us figure out if
the tag system is skewed against certain combinations._

`indpeendence_delta_data` are the output files of this work. Values are
calculated as `P(A)P(B) - P(A & B)`. The closer each cell is to 0, the more
independent they are. The higher each cell is, the lower the rate of `P(A & B)`,
which implies that they show up less frequently together than if they were
independent. This implies that the two tags are thus explicitly weighted such
that they appear less often together. Likewise, if the values are very positive,
this implies that they are weighted to show up more frequently together.

## Conclusions

For most of the tag combinations, we see that many have an absolute difference
of anywhere from `0.002` to `0.00003`, which imply that they are very likely to
be independent, and that the differences can be attributed to noise in data
collection. However, there are a few notable cells that are worthwhile to
discuss.

Given the data, we can conclude that there is a bias _against_ guaranteed 4 star
and up tag combinations. For example, we see that certain tag combinations
like Supporter and DPS (Istina), have a difference of `+0.05` between its
independent rates. We see that this also occurs with Guard/Aoe (Estelle/Specter),
Melee/Healing (Gummy/Nearl), and Survival/Ranged (Jessica), to name a few.

We also see that some tags have a slight chance to appear more frequently with
each other: notably, Defense/Defender seem to have a difference of `-0.03`,
and Melee/Guard to have a `-0.01` difference as well.

For posterity, we should mention that the diagonal cells (e.g. AoE/AoE. DPS/DPS,
etc.) have nonsensical values, as they're artifacts of the calculations. These
values can be ignored because it's impossible to have identical tags show up in
a single roll.

However, we refuse to make conclusions about tag independence with regards to
the rarer tags, such as Nuker, Top, and Summon, due to the small sample size.

Finally, we discuss the primary source of bias, self-selection bias. We would
expect many users to post "interesting" results over all results, which means
that people are likely to post guaranteed 4* or 5* tag combinations more so than
tag combinations that don't guarantee anything. However, we see that the rarer
tag values are already positive. This implies that even with self-selection
bias present, we see that the tag combinations are already biased towards
not showing up with each other. This means that if anything, it's likely that
the tag combinations are even more rare than reported.

[reddit-user]: https://old.reddit.com/user/patrickpeng168
[reddit]: https://old.reddit.com/r/arknights/comments/fclfig/discussion_update_11000_recruit_tags_later/
