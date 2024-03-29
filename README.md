
# ScaleThem!

**ScaleThem!** is a simple VRChat prefab that allows you to scale yourself or other players in your VRChat world. Just drag and drop the prefab, configure it and it's all done! It's easy to setup and syncs for the players and late joiners.

![Capture d'écran 2024-03-29 121433](https://github.com/BloomingTails/ScaleThem/assets/77898978/85056da3-82c0-41bd-b0ce-d8b61754580a)

This prefab was made as a proof of concept in mind, so there's not a lot of features. Just keep in mind that if you have other prefabs in your scene messing with AvatarScaling, it may conflict with it!

Feel free to edit the UI as it is pretty simple but please keep me credited, thank you!



# How to use

You will find two prefabs in your Unity project located in `Assets/BloomingPrefabs/ScaleThem!/Prefabs`:

## ScaleThemMaster

**ScaleThemMaster** works with the master of the Instance: The master will have full control over the prefab, and others won't. If the master leaves the instance, it will transfer the controls to the new Master.

1. Drop the **ScaleThemMaster** prefab in your scene.

2. Go to the **AvatarScaleEnabler** GameObject and decide whether or not you will allow all players (including the master) from resetting their avatar scaling by enabling/disabling the **allowManualScaling** bool.

3. Go to the **SliderScale** GameObject and adjust the **Min Value** and **Max Value** on the **Slider** component to set the values that the slider will be able to select, aka minimum and maximum scale. (Note that you shouldn't set the **Min Value** to **0**, as this won't work in-game and will reset your height).

4. Done!

## ScaleThemNickname

**ScaleThemNickname** works with one unique player based on their VRChat username/display name: They will have full control over the prefab, and everyone else won't. If the granted player leaves the instance, it will not transfer the controls to anyone, and only that player can use it if they join the instance again.

1. Drop the **ScaleThemNickname** prefab in your scene.

2. Go to the following GameObjects and change the **VRChatPlayerNickname** string to the desired player's name (make sure to match it exactly or it won't work):

    -**AvatarScaleEnabler**

    -**SliderScale**

3. Go to the **AvatarScaleEnabler** GameObject and set the **Granted** and **Refused** strings. This will appear in the bottom left corner of the prefab to let the player know if they are or not the granted player (Can be left empty for no text).

4. Still on the **AvatarScaleEnabler** GameObject, decide whether or not you will allow all players (including the granted player) from resetting their avatar scaling by enabling/disabling the **allowManualScaling** bool.

5. Go to the **SliderScale** GameObject and adjust the **Min Value** and **Max Value** on the **Slider** component to set the values that the slider will be able to select, aka minimum and maximum scale. (Note that you shouldn't set the **Min Value** to **0**, as this won't work in-game and will reset your height).

6. Done!

# Extra Notes

There are some settings that you can adjust inside each Udon Graphs that are not exposed in the public fields of the Udon Behaviour, such as the delays of the **SendCustomEvents** and such.

I've added a **OnPlayerJoined** that fires a **SendCustomEvent** with a 3 seconds delay to apply the scale of a local player whenever one joins the instance, leaving enough time for the player to load their avatar. It's just there as a fallback as I did use a **OnAvatarChanged** on top of that.
