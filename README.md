<p align="center">
  <img alt="UnrealEngineLogo" src="https://cdn2.unrealengine.com/ue-logo-stacked-unreal-engine-w-677x545-fac11de0943f.png" width="375px">
</p>

# Informations 📜
- This component has been developed and utilized in Unreal Engine 5.3.2. It is compatible with Unreal Engine 5.X ([Unreal Engine](https://www.unrealengine.com/))
- It is designed for use with a third-person character blueprint featuring animations.
- The component is developed using a single Blueprint and is customizable (Blueprint count: 1)
- It is not compatible with AI

# Table of contents

- [Informations 📜](#informations-)
- [Table of contents](#table-of-contents)
- [Documentation 🗎](#documentation-)
  - [Start 🎬](#start-)
  - [Initialize with character animations 🧝](#initialize-with-character-animations-)
  - [Call FootMontage Functions 📲](#call-footmontage-functions-)
  - [Foot Sounds 🌎](#foot-sounds-)
  - [Customize 🆕](#customize-)

## Documentation 🗎

## Start 🎬
- Download [this repository](https://github.com/17mylan/FootManagerComponent/)
- Add the file named "FootManager" to the Content File of your project
- Add the component named "FootManager" inside of your character blueprint ![image](https://github.com/17mylan/Experimental/assets/89989070/32c2fe5c-4aa6-4a4a-a8fc-9370788e274a)

## Initialize with character animations 🧝
- Open your animations where the player needs to use the FootManager component (e.g., Walk, Run)
- Create 2 Animation Notifiers (one for the left foot and one for the right foot). The documentation uses predefined Unreal animation notifiers such as "l_foot_plant" and "r_foot_plant" 
![image](https://github.com/17mylan/Experimental/assets/89989070/a5c83c8d-0866-47a1-8f4f-6ac2870f43d0)

- Place your animation notifiers to be timed when the character steps on the floor
![image](https://github.com/17mylan/Experimental/assets/89989070/adcf4e9d-2301-400a-af50-ec54c7c7fb4e)

## Call FootMontage Functions 📲
- Go to your character animation blueprint and create or use the character blueprint reference where you have [set up](#start-) the "FootManager" component
- Using your [animation notifiers](#initialize-with-character-animations-), get "FootManager" component and call function named "FootManager"
- Ensure that you assign the correct foot with the animation notifiers (e.g., the left animation notifier should be called when the character's left foot is on the floor in the animation)
![image](https://github.com/17mylan/Experimental/assets/89989070/b40ade04-50ee-4f70-8bde-bb2321db8589)

## Foot Sounds 🌎
- To create custom sounds based on character floor environment, navigate to:
> Project settings > Physics > Physical Surface > Add new physical Surface Name (e.g, Dirt)

![image](https://github.com/17mylan/Experimental/assets/89989070/2ecd8acf-11c5-40ae-b381-2de8db4af978)

- Create new Physical Material
> Physics > Physical Material > PhysicalMaterial

![image](https://github.com/17mylan/Experimental/assets/89989070/6a7b206a-88bd-40ad-acfa-ed520352ae6d)

- Open your new Physical Material and set the value of "Surface Type" to the new Surface material you [created in the project settings](#foot-sounds-) (e.g., Dirt)
![image](https://github.com/17mylan/Experimental/assets/89989070/fc25a575-2194-4e77-802d-cc9e326b0312)

- Add your new Physical Material to your environment (e.g., Plane) in the "Physical Material Override" section of the collision preset
![image](https://github.com/17mylan/Experimental/assets/89989070/e695336a-f732-4ede-9b27-2e51793b32cd)

- Add a new step sounds list value by selecting your new surface type and assign your footstep sound inside your [character blueprint component named "FootManager"](#start-)
![image](https://github.com/17mylan/Experimental/assets/89989070/a0ddd37c-8a80-479b-818d-b04bb4f1b3f6)

## Customize 🆕
- In your character blueprint, select the component named "FootManager" in the components window. In the details window, you can now customize the values as desired
![image](https://github.com/17mylan/Experimental/assets/89989070/24196003-7a39-47fa-a301-86162ef8fb5d)
> Component Active?: Enable or disable the component

> Print Foot Step Decal?: Enable or disable the functionality to print foot decals on the ground

> Decals Parameters: Customize the material, trace line-to-feet distance, character's foot sockets and socket rotation adjustment, foot decal size and foot decal duration

> Play Foot Step Sound?: Enable or disable the functionality to play foot step sound

> Sounds Parameters: Customize the rotation, volume multiplier, pitch multiplier, start time, attenuation settings, concurrency settings, initials params and step sounds list
