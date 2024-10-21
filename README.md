<p align="center">
  <img alt="UnrealEngineLogo" src="https://cdn2.unrealengine.com/ue-logo-stacked-unreal-engine-w-677x545-fac11de0943f.png" width="375px">
</p>

# Informations 📜
- Customizable Unreal Engine component for generating footprints and footsteps sounds based on character environment.
- This component has been developed and utilized in Unreal Engine 5.4.4. ([Unreal Engine](https://www.unrealengine.com/))
- It's designed for use with a third-person character blueprint featuring animations.
- The component is developed using a single Blueprint Component and is customizable (Blueprint Component count: 1)
- It's compatible with AI (using Character Class)

# Table of contents

- [Informations 📜](#informations-)
- [Table of contents](#table-of-contents)
- [Documentation 🗎](#documentation-)
  - [Start 🎬](#start-)
  - [Initialize with character and AI animations 🧝](#initialize-with-character-and-ai-animations-)
  - [Call FootManager Functions 📲](#call-footmanager-functions-)
  - [Foot Sounds 🌎](#foot-sounds-)
  - [Circle Decal ⭕](#circle-decal-)
  - [Customize 🆕](#customize-)
  - [Events 🎫](#events-)

## Documentation 🗎

## Start 🎬
- Download [this repository](https://github.com/17mylan/FootManagerComponent/) or from [Unreal Engine Marketplace](https://github.com/17mylan/FootManagerComponent/) (Not accessible at the moment)
- If you downloaded the plugin from GitHub, install the un-zipped file named "FootManager" in your Unreal Project Plugins File. (e.g, D:\Unreal Projects\YourProjectName\Plugins). Create the "Plugins" File you don't have one.
- Start your project and enable the plugin
> Settings > Plugins > FootManager > Enable and restart your editor
![image](https://github.com/user-attachments/assets/bc4ecbdf-6ba3-4fb7-8c6f-dfc45f6f18d9)
  
## Initialize with character and AI animations 🧝
- Add the component named "FootManager" inside of your character/AI blueprint ![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/00bd509f-4441-49b8-ac5b-1f599bad335d)
- Open your animations blueprint where the player needs to use the FootManager component (e.g., Walk, Run)
- Create 2 Animation Notifiers (one for the left foot and one for the right foot). The documentation uses predefined Unreal animation notifiers such as "l_foot_plant" and "r_foot_plant" 
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/2d6411ba-c17b-4d7e-b440-10a6e369515d)

- Place your animation notifiers to be timed when the character steps on the floor
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/753fc2dd-1297-43a1-a2a3-f031dc7b81b0)

## Call FootManager Functions 📲
- Go to your character/AI animation blueprint and create or use the character/AI blueprint reference where you have [set up](#start-) the "FootManager" component
- Using your [animation notifiers](#initialize-with-character-animations-), call the function named "Call Foot Manager" and assign the character variable to the function
- Ensure that you assign the correct foot with the animation notifiers (e.g., the left animation notifier should be called when the character's left foot is on the floor in the animation)
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/999bf482-d69d-4a77-af24-2b4a24ce9923)

## Foot Sounds 🌎
- To create custom sounds based on character/AI floor environment, navigate to:
> Project settings > Physics > Physical Surface > Add new physical Surface Name (e.g, Dirt)

  ![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/a20bce4d-515a-4ac1-97d5-803acc5ce005)

- Create new Physical Material
> Physics > Physical Material > PhysicalMaterial

  ![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/4fb773ad-56c7-4515-9cc7-085c142396dd)

- Open your new Physical Material and set the value of "Surface Type" to the new Surface material you [created in the project settings](#foot-sounds-) (e.g., Dirt)

  ![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/c3f7cc28-8a84-4cb3-a562-2b8b1bc14864)

- Add your new Physical Material to your environment (e.g., Plane) in the "Physical Material Override" section of the collision preset
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/2b3e7ce3-9969-4670-a7e6-aa73f02a0ed3)

- Add a new step sounds list value by selecting your new surface type and assign your footstep sound inside your [character/AI blueprint component named "FootManager"](#start-)
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/74f00a04-8a7a-4b14-a04b-5452f7971726)

## Circle Decal ⭕

- Display only 1 circle as material on the ground. The circle stay on the ground whenever the player is in the air.
- The decal do not tick when the player is on the ground but tick when the player is falling (Tick use GetWorldDeltaSeconds Interval).
![image](https://github.com/user-attachments/assets/13aa2abe-1d0e-4635-9a15-208151939e95)

- Go to your character's/AI blueprint. Call the event named "Event OnMovementModeChanged" and link this event to the FootManager Event named "FootManagerOnMovementModeChanged"
![image](https://github.com/user-attachments/assets/94057239-9563-4a17-8aba-69a17b2fc54f)

- Add "Decal" to your blueprint and set it to be child of your mesh. Add the tag "CircleDecal" on your decal component tag (The tag can be changed but you need to have the same tag as FootManager > PrintCircleDecal > CircleParameters > CircleDecalTag) The tag is used to identify and use the correct decal.
- Change your decal's values as you need (For the demonstration, FootManager CircleDecal use these values to work properly)
![image](https://github.com/user-attachments/assets/e46f2379-88c1-4aaa-81af-3207478c0678)

- Select your character's/AI mesh and disable the "Receives Decals" option
![image](https://github.com/user-attachments/assets/83800f19-08a1-48ad-acee-a749fac194a4)

- To customize your decal, you can create a material and set it to "Deffered Decal" as material domain and blend mode to "Translucent"
- Make sur to copy the same material from the picture and use the same Param Names ("Color" & "Intensity". Color & Intensity are used to determine your color and normal intensity on the FootManager Component on your blueprint). You can change the texture as you need.
- Once it's done, make sure to create a Material Instance of your material and assign it to FootManager > PrintCircleDecal > CircleParameters > CircleDecalMaterial.
![image](https://github.com/user-attachments/assets/6d00cd48-a52a-4ab9-8274-8a7fa9219f78)

## Customize 🆕
- In your character/AI blueprint, select the component named "FootManager" in the components window. In the details window, you can now customize the values as desired
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/68669e82-0db6-4260-af95-1f915c67bbe1)

> Component Active?: Enable or disable the component

> Print Foot Step Decal: Enable or disable the feature to print foot decals on the ground

> Decals Parameters: Customize the material, trace line-to-feet distance, character's foot sockets and socket rotation adjustment, foot decal size and foot decal duration

> Play Foot Step Sound: Enable or disable the feature to play foot step sound

> Sounds Parameters: Customize the rotation, volume multiplier, pitch multiplier, start time, attenuation settings, concurrency settings, initials params and step sounds list

> Play Foot Step VFX: Enable or disable the feature

> VFX Parameters: Customize the VFX Method (using Niagara System or Particle System), rotation and scale

> Enable Circle Decal: Enable or disable the feature

> Circle Parameters: Customize the CircleDecalTag, material, trace line-to-feet distance, circle intensity, circle jump intensity, circle color, play circle jump animation and jump animation scale

## Events 🎫
- It's possible to use foot manager events when a character or AI triggers one. (You can also use the "Assign" method in other blueprints)

![image](https://github.com/user-attachments/assets/f0119cf3-7314-4b58-bce9-abbeff9079e0)

> Examples and ideas of what you can do with these events:

![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/31aa6409-d818-4964-aefe-d6603c312567)

