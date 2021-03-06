---
layout: page
header: no

permalink: /physics-driven-animation

title:  "Hairibar.Ragdoll: Physics-Driven Animation"
teaser: "A Unity package that drives ragdolls and makes them play keyframed animations while keeping physics behaviour. Also, my thesis."

image:
    thumb: TFG\TFG_DignifiedSidewalk.gif

breadcrumb: false
show_meta: false

category: My Work
tags:
    - featured

look-at-code-button:
  text: Look at the code
  url: https://github.com/hairibar/Hairibar.Ragdoll

read-thesis-button:
  text: Read the thesis
  url: /assets/hosted-files/Physics-Driven Character Animation.pdf
---

{%include YoutubeVideo.html embedURL="https://www.youtube.com/embed/ByNPbbACf40"%}

## It's versatile.
- Free your animators from the tedious labour of hand-animating secondary motion.
- Use it with tight settings to get realistic characters that react to collisions.
- Use it with loose settings to get silly, physicsy motion.

{% include VideoEmbed.html video="TFG/TFG_UndignifiedSidewalk.webm" type="webm" autoplay = true %}
{% include alert text="I <strong>did</strong> say silly, right?"%}

{% include VideoEmbed.html video="TFG/TFG_Hanging.mp4"  type="mp4" autoplay = true  %}
{% include alert text="You can use it in plenty of situations. Here, the right hand is locked - pure animation, no physics. There is only one frame of animation in this video - the rest of the moment is just physics." %}

## It's transparent.
The system lets the existing animation tech do its work, reads the resulting pose and then drives the ragdoll towards that pose. 

This makes it inherently compatible with any system that modifies animation, such as IK. 
![]({{site.urlimg}}/TFG/TFG_Inspector_Transparent.png)

## It's easy to use.
Most configuration is done through artist-friendly `ScriptableObjects`. Their editors have been heavily customized to make them easy and safe to use.

Most parameters are sliders that go from 0 to 1, with clearly explained effects.
![An example of a RagdollAnimationProfile]({{site.urlimg}}/TFG/TFG_Inspector_DignifiedRaganim.png)

## It's generic.
Unlike with many of Unity's animation features, all rig types are supported, not just humanoids. 

The available bones are listed in a `RagdollDefinition` asset. After that, per-individual-bone parameters can be set in other assets, such as `RagdollAnimationProfile` and `RagdollWeightDistribution`.
<div class="row">
  <div class="small-12 large-6 column t10">
    <img src="{{site.urlimg}}/TFG/TFG_Inspector_ChickenRagdef.png"/>
  </div>
  <div class="small-12 large-6 column t10">
    <img src="{{site.urlimg}}/TFG/TFG_Inspector_ChickenRagwgt.png"/>
  </div>
</div>

## It's expandable.
Writing scripts that modify the ragdoll's behaviour is supported. 

You can implement `IBoneProfileModifier` to dynamically affect the way the ragdoll matches the animation, or you can implement `ITargetPoseModifier` to post-process the pose that the regular animation system has provided before the ragdoll follows it. Many of the built-in features have been implemented through these interfaces!
![]({{site.urlimg}}/TFG/TFG_Inspector_Modifiers.png)

You can also make your own data types that work with specific `RagdollDefinitions`, in case your modifiers need to be easily-configurable. Just inherit `RagdollProfile`!

## It's integrated with Mecanim.
Hairibar.Ragdoll comes with `StateMachineBehaviours` like `SetRagdollAnimationProfileOnEnter` and `SetRagdollPowerProfileOnEnter`. These behaviours allow you to easily tie specific sets of parameters to specific animation states.
![]({{site.urlimg}}/TFG/TFG_Inspector_Mecanim.png)

## Okay, so how do I get it?
It's publicly hosted in [GitHub](https://github.com/hairibar/Hairibar.Ragdoll), and distributed via Unity's Package Manager. You can add it to your projects by adding the following lines to your manifest.json:
{% highlight javascript %}
{
  "dependencies": {
    ...
    "com.hairibar.naughtyattributes": "https://github.com/hairibar/NaughtyAttributes.git#v2.2.1",
    "com.hairibar.engineextensions": "https://github.com/hairibar/Hairibar.EngineExtensions.git#v1.2.2",
    "com.hairibar.ragdoll": "https://github.com/hairibar/Hairibar.Ragdoll.git#upm"
    ...
  }
}
{% endhighlight %}

More detailed instructions (and possibly more up to date ones, too) can be found at the [repository itself](https://github.com/hairibar/Hairibar.Ragdoll).

## How does it work?
Hairibar.Ragdoll was my end-of-degree project. For an in-depth look, you can read the thesis [here]({{ site.url }}/assets/hosted-files/Physics-Driven Character Animation.pdf).
A demo project and a manual are coming in the future.

{% include GuideButton.html button=page.look-at-code-button %}
{% include GuideButton.html button=page.read-thesis-button %}
