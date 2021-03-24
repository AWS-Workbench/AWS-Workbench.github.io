

# AWS Workbench getting started guide

1. Open Obeo Designer 
2. Create a new modelling project 
- ``` Right Click on Project Explorer -> New -> Modelling Project   ```
- Enter the name of the project.
- Click  ```Finish```
- [Demo clip](../images/getting-started-images/create-project.gif)
3. Create a new AwsWorkbench model 
- ```Right click on project -> New -> Other```
- Select ```AWSWorkbench model``` from the ```Select Wizard```. Click ```Next```
- Type the name of the awsworkbench model.  Click ```Next```
- Select ```App Builder core``` from the dropdown list. Click ```Finish```.
- [Demo clip](../images/getting-started-images/create-app-workbench.gif)
4. Create the App Diagram. 
- ```Expand Project Tree -> Select App null node -> Right Click App null node -> New Representation -> Other ```
- Select ```AWS App Definition``` and click ```Finish```
- Type a name for your diagram and click ```OK```
- [Demo clip](../images/getting-started-images/create-app-diagram.gif)
5. Create Stack 
- An app is made up of one or more stacks
- In the **App Diagram Canvas** drag an ```Environment``` object from the tools pallette and configure it using the [properties editor](./properties-editor.md). 
- In the **App Diagram Canvas** drag an ```Stack``` object from the tools pallette and configure it using the [properties editor](./properties-editor.md). Enter the *varName* of **Environment** object in the ```env``` property for the Stack. 
- [Demo clip](../images/getting-started-images/stack-creation.gif)
6. Create Blocks
- Stack are made up of one or more ```Blocks```. **Blocks** are constructs used to group AWS services. Block may have ```Sub Blocks```
- Double Click on Stack to create a new Stack Tab. Navigate to Stack Tab and create multiple blocks based on your architecture. You can also create Sub Blocks inside Blocks. 
- *Block* has a property called ```canDeploy```. Until the value of **canDeploy** is ```true```, Block content is in *draft* state and the corresponding code ***will not be exported***. Neither the elements from the Block can be referenced in other blocks. 
- [Demo clip](../images/getting-started-images/block-creation.gif)
7. Creating services
-  Once the skeleton of your infrastructure is ready, you can start adding services to the Blocks. 
- Double Click the Block in which you wish to add services ad create a new Tab for the Block. 
- On the right, you can see the Services arranged in alphabetical order. 
- Drag and drop the services on the Block and configure using [properties editor](./properties-editor.md).
- [Demo clip](../images/getting-started-images/creating-services.gif)
8. After defining all the components, follow the [quick start tutorial](./quick-start.md#generate-java-code) to generate code and deploy. 
      




