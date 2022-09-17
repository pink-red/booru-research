# booru-research

## Current state of affair
- posts have tags
- search by set operations

## Relations between nodes instead of tags
- structured description of actors, readily reuseable
- much more detailed situation description with graphs

Inference on graphs
- prolog

## Booru interconnectivity — namespaces
- different meanings for tags in different boorus
- https://arxiv.org/abs/2206.04453


## Nested contexts

- global
  - some girl
    - `long_hair`

Inside a context there can't be conflicts. If there's `long_hair`, there can't be `short_hair`.

If there's enough information, it is possible to pull tags to the global context. For example, if we know that there's only one girl in a post, we know that whole post contains only `long_hair` and can't have `short_hair` tag.

- global
  - `1girl`
  - `solo`
  - `long_hair`


## Disjoint tags

Some tags are disjoint


## Negative tags

Sometimes it is useful to have information about abscence of things. Some users would only be interested in posts involving humans (no monsters, tentacles, etc.) Sankaku Channel has an [human_only tag](https://chan.sankakucomplex.com/?tags=human_only&commit=Search), for example.

A negative tag also disambiguates abscence of another tag. For example, a negative `solo` tag would mean that there are multiple people, but wouldn't say how many. On the other hand, abscence of the `solo` tag could mean either that there's definitely multiple people or that this tag is simply missing and it's unknown how many people there are.

> I would say that the Danbooru tag data is quite high but imbalanced: almost all tags on images are correct, but the absence of a tag is often wrong—that is, many tags are missing on Danbooru (there are so many possible tags that no user could possibly know them all). So the absence of a tag isn’t as informative as the presence of a tag—eyeballing images and some rarer tags, I would guess that tags are present <10% of the time they should be.

https://www.gwern.net/Danbooru2021#metadata-quality-improvement-via-active-learning
