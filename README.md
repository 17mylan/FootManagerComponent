<p align="center">
  <img alt="UnrealEngineLogo" src="https://cdn2.unrealengine.com/ue-logo-stacked-unreal-engine-w-677x545-fac11de0943f.png" width="375px">
</p>

# Informations 📜
- Customizable Unreal Engine component for generating footprints and footsteps sounds based on character environment.
- This component has been developed and utilized in Unreal Engine 5.3.2. It is compatible with Unreal Engine 5.X ([Unreal Engine](https://www.unrealengine.com/))
- It is designed for use with a third-person character blueprint featuring animations.
- The component is developed using a single Blueprint and is customizable (Blueprint count: 1)
- It is compatible with AI (Character Class)

# Table of contents

- [Informations 📜](#informations-)
- [Table of contents](#table-of-contents)
- [Documentation 🗎](#documentation-)
  - [Start 🎬](#start-)
  - [Initialize with character animations 🧝](#initialize-with-character-animations-)
  - [Call FootManager Functions 📲](#call-footmanager-functions-)
  - [Foot Sounds 🌎](#foot-sounds-)
  - [Customize 🆕](#customize-)

## Documentation 🗎

## Start 🎬
- Download [this repository](https://github.com/17mylan/FootManagerComponent/)
- Add the file named "FootManager" to the Content File of your project
- Add the component named "FootManager" inside of your character blueprint ![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/00bd509f-4441-49b8-ac5b-1f599bad335d)
## Initialize with character animations 🧝
- Open your animations where the player needs to use the FootManager component (e.g., Walk, Run)
- Create 2 Animation Notifiers (one for the left foot and one for the right foot). The documentation uses predefined Unreal animation notifiers such as "l_foot_plant" and "r_foot_plant" 
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/2d6411ba-c17b-4d7e-b440-10a6e369515d)

- Place your animation notifiers to be timed when the character steps on the floor
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/753fc2dd-1297-43a1-a2a3-f031dc7b81b0)

## Call FootManager Functions 📲
- Go to your character animation blueprint and create or use the character blueprint reference where you have [set up](#start-) the "FootManager" component
- Using your [animation notifiers](#initialize-with-character-animations-), call the function named "Call Foot Manager" and assign the character variable to the function
- Ensure that you assign the correct foot with the animation notifiers (e.g., the left animation notifier should be called when the character's left foot is on the floor in the animation)
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/999bf482-d69d-4a77-af24-2b4a24ce9923)

## Foot Sounds 🌎
- To create custom sounds based on character floor environment, navigate to:
> Project settings > Physics > Physical Surface > Add new physical Surface Name (e.g, Dirt)

  ![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/a20bce4d-515a-4ac1-97d5-803acc5ce005)

- Create new Physical Material
> Physics > Physical Material > PhysicalMaterial

  ![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/4fb773ad-56c7-4515-9cc7-085c142396dd)

- Open your new Physical Material and set the value of "Surface Type" to the new Surface material you [created in the project settings](#foot-sounds-) (e.g., Dirt)

  ![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/c3f7cc28-8a84-4cb3-a562-2b8b1bc14864)

- Add your new Physical Material to your environment (e.g., Plane) in the "Physical Material Override" section of the collision preset
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/2b3e7ce3-9969-4670-a7e6-aa73f02a0ed3)

- Add a new step sounds list value by selecting your new surface type and assign your footstep sound inside your [character blueprint component named "FootManager"](#start-)
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/74f00a04-8a7a-4b14-a04b-5452f7971726)

## Customize 🆕
- In your character blueprint, select the component named "FootManager" in the components window. In the details window, you can now customize the values as desired
![image](https://github.com/17mylan/FootManagerComponent/assets/89989070/8db59d68-826c-405a-b0ac-3d32ee2d5276)

> Component Active?: Enable or disable the component

> Print Foot Step Decal?: Enable or disable the functionality to print foot decals on the ground

> Decals Parameters: Customize the material, trace line-to-feet distance, character's foot sockets and socket rotation adjustment, foot decal size and foot decal duration

> Play Foot Step Sound?: Enable or disable the functionality to play foot step sound

> Sounds Parameters: Customize the rotation, volume multiplier, pitch multiplier, start time, attenuation settings, concurrency settings, initials params and step sounds list
