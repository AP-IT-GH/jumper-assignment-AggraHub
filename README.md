# Jumper Opdracht
## Start een Unity Project op
1. Start Unity Hub, selecteer 3D en geef ze een naam
![image](https://user-images.githubusercontent.com/104986603/233506502-662d2c2b-5832-4c07-a67c-08c0bf52b498.png)
2. Eens opgestart, zorg dat je de ML Agents pakket instaleer met uw package manager. Je 'Packages: In Project' tab zou er ongeveer als volgt moeten uitzien.
![image](https://user-images.githubusercontent.com/104986603/233506844-23d831ab-d55c-4fe7-969e-30fc23410094.png)

Importeer ook zeker de [Modular Lowpoly Streets](https://assetstore.unity.com/packages/3d/environments/urban/modular-lowpoly-streets-free-192094) want dit zijn de prefabs die we zullen gebruiken.

## Opstellen van je scene

1. Begin met een het plaatsen van een 'Crossroads_1_lines_walk' en noem deze 'Crossroads'. Geef ze de volgende configuratie

![image](https://user-images.githubusercontent.com/104986603/233508736-c4a3894a-6247-4c5d-8e56-1a8e85dc44c1.png)

Alles zal relatief werken tegenover deze vloer.

2. Voeg nu de Agent toe. Dit is hetgeen dat we gaan trainen om de obstacles te ontwijken en de coins te pakken

![image](https://user-images.githubusercontent.com/104986603/233509773-d6d583f3-a069-4173-a4a1-19cc76b48932.png)
![image](https://user-images.githubusercontent.com/104986603/233509797-c06d3961-bfe9-41b2-95c2-fdc7b6bd15a0.png)
![image](https://user-images.githubusercontent.com/104986603/233509807-78f0fe1d-e44b-4477-a429-fc64bae92a41.png)

Het materiaal dat je ze geeft heeft geen invloed op resultaten. Voel u vrij om met de waardes in Sphere Agent en in Ray Perception te spelen.

3. Voeg nu een coin toe. Dit zal een beloning geven aan de Agent. Geef ze de volgende configuratie

![image](https://user-images.githubusercontent.com/104986603/233510871-f98eb801-ddfd-4eab-a4e1-3df5b3a25d33.png)

4. Nu maken we de obstacles. Dit is wat the Agent dient te ontwijken en zullen gespawnt worden elke keer als de episode begint of zolang de Agent ze blijft ontwijken.

![image](https://user-images.githubusercontent.com/104986603/233511113-43eac759-2f68-4c2f-ae7f-50d499684fae.png)

5. maken van de straten. hier zetten bij 2 van de 4 ook een Spawner. Een Spawner is wat de de verschillende Obstacles zal spawnen en op de agent te richten. Deze straten noemen we dan ObstacleParkour

![image](https://user-images.githubusercontent.com/104986603/233513051-271016a6-a1f9-4127-b220-f9d837748831.png)
![image](https://user-images.githubusercontent.com/104986603/233513332-16d27d0d-e000-4d0b-83bf-dab1ffe625da.png)

Geef 2 naast mekaar liggende straten een Spawner.

## de scripts

De SpawnCube is wat de obstacles zal spawnen en sturen naar de Agent. SphereAgent is where the magic happens, hier is het script dat het bedrag en de beloning voor de Agent beschrijft.

Vervolgens heb je nog je yaml file die er als volgt uit ziet:

![image](https://user-images.githubusercontent.com/104986603/233515986-00eb581c-0204-47b8-83f4-ad2baecf440c.png)

Deze agent heeft voldoende tijd nodig om te leren, vandaar het grote aantal stappen

## opzetten van anaconda

Het is nodig om Anaconda (prompt) te installeren om je agent te kunnen trainen. Je kunt de instructies vinden op anaconda.com.

Om PyTorch te installeren op Windows, open je de Anaconda prompt en voer je het volgende commando uit: pip3 install torch~=1.7.1 -f https://download.pytorch.org/whl/torch_stable.html.

Om ML Agents te installeren, voer je het volgende commando uit: python -m pip install mlagents==0.28.0.

Om te controleren of de installatie is geslaagd, voer je het commando mlagents-learn --help uit.

## trainen van de agent

Om je agent te trainen, open je twee tabbladen in Anaconda Prompt en navigeer je in beide tabbladen naar de Assets-map van je Unity-project, waar de config-map zich bevindt.

In het eerste tabblad voer je het volgende commando uit: mlagents-learn config/JumperAgent.yaml --run-id=Agenttraining. Je kunt uiteraard zelf de naam van de run-id kiezen.

In het andere tabblad voer je het volgende commando uit: tensorboard --logdir results.




