# Booru Research

## Current state of affair
- posts have tags
- search by set operations

## Relations between nodes instead of tags
- structured description of actors, readily reuseable
- much more detailed situation description with graphs

Inference on graphs
- prolog


## Booru interconnectivity

> Each of these datasets has its own set of class labels, its own visual definition for each class, its own set of images following a specific distribution, its own annotation protocols, and was labeled by a different group of humans annotators. As a result, the visual-semantical meaning of a certain label in a particular dataset is unique.

> Are [labels] in an identity, parent/child, overlap relation? Or is there no link between them at all?

https://arxiv.org/abs/2206.04453

The problems include:

- tags with the same name have different meanings in different boorus
- tags with different names have same meaning in different boorus
- some boorus differentiate more varieties of a tag, while other have only one tag

### Namespaces

One solution to this problem would be to differentiate tags from different boorus. For example, to put them into corresponding namespaces.

- `danbooru/head_back`
- `sankakuchannel/head_thrown_back`


### Relations between tags of different boorus

> ![image](/label-relations.png)
> Fig. 1: Examples of relations: (a) identity: both bicycle labels contain similar instances; (b) parent/child: the animal class contains instances which are either cat or dog; (c) floor and rug-merged overlap in the middle instance. But each label contains instances which are incompatible with the other label.

https://arxiv.org/abs/2206.04453



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

Some tags are disjoint, for example `1girl` and `2girls`. They can't be present in a post at the same time. Knowing which tags are disjoint could help to find and correct tagging errors, and also to automate tagging.

For example, if there's `1girl` tag in a post, we could say that this tag has 100% probability. Then, `2girls`, `3girls`, etc. would have 0% probability. When training an automated tagger, such as [DeepDanbooru](https://github.com/KichangKim/DeepDanbooru), we could assign 1 to `1girl` and 0 to `2girls` and the others. Absent tags would have probability of 0.5, meaning that it's unknown if they are definitely present or deliberately absent.


> Statement: "Mary" "is a citizen of" "France"
>
> Question: Is Paul a citizen of France?
>
> "Closed world" (for example SQL) answer: No.  
> "Open world" answer: Unknown.

https://en.wikipedia.org/wiki/Open-world_assumption


## Negative tags

Sometimes it is useful to have information about abscence of things. Some users would only be interested in posts involving humans (no monsters, tentacles, etc.) Sankaku Channel has an [human_only tag](https://chan.sankakucomplex.com/?tags=human_only&commit=Search), for example.

A negative tag also disambiguates abscence of another tag. For example, a negative `solo` tag would mean that there are multiple people, but wouldn't say how many. On the other hand, abscence of the `solo` tag could mean either that there's definitely multiple people or that this tag is simply missing and it's unknown how many people there are.

> I would say that the Danbooru tag data is quite high but imbalanced: almost all tags on images are correct, but the absence of a tag is often wrong—that is, many tags are missing on Danbooru (there are so many possible tags that no user could possibly know them all). So the absence of a tag isn’t as informative as the presence of a tag—eyeballing images and some rarer tags, I would guess that tags are present <10% of the time they should be.

https://www.gwern.net/Danbooru2021#metadata-quality-improvement-via-active-learning
