# DynamicsCrm-CodeGenerator

[![Join the chat at https://gitter.im/yagasoft/DynamicsCrm-CodeGenerator](https://badges.gitter.im/yagasoft/DynamicsCrm-CodeGenerator.svg)](https://gitter.im/yagasoft/DynamicsCrm-CodeGenerator?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

---

A Visual Studio extension for generating early bound classes for Microsoft Dynamics CRM entities based on a template file, similar to Entity Framework.

## Features

  + Built for Visual Studio
    + You never have to leave Visual Studio to regenerate the code
	+ All the configurations are saved in the project itself, which facilitates Version Control
  + Preserved the original CrmSvcUtil structure and logic
  + Customize the way the code is generated
    + You get a default T4 template for the code that is generated, with a multitude more features than the official tool (features below)
	+ You can rewrite the whole template if you wish for any possible requirements
  + Replaced the SDK types with .NET types
    + E.g. OptionSetValue => Enum (Enum[] for Multi-select), EntityReference => Guid, Money => decimal, ... etc.
  + Generate only what's needed
    + Only choose the entities required
    + Only the fields required
  + Additional control
    + Option to use display names of entities and fields as variable names instead of logical names
    + Override field names inside the tool's UI
    + Ability to Lock variable names to avoid code errors on regeneration
  + Greatly enhanced regeneration speed by only fetching changed metadata from the server
  + Support for strongly-typed alternate keys, for entities and Entity References
  + Add annotations for model validation
  + Generate metadata
    + Field logical and schema names
    + Localised labels
  + Automatically limit attributes retrieved from CRM on any entity in a LINQ to the ones choosen (filtered) in the tool (check new entity constructors)
  + Many options to optimise generated code size even further
  + Define web service contracts with different profiles
    + Option to mark certain fields as 'read-only'
    + Option to link CRM entity profile with contract profiles, which effectively copies selection changes made in contracts to the CRM entity
  + Generate concrete classes for CRM Actions
  + Support bulk relation loading
    + Support filtering on relation loading

This tool is available as an XrmToolBox plugin as well ([here](https://www.xrmtoolbox.com/plugins/plugininfo/?id=45abdb43-f0e5-ea11-bf21-281878877ebf)).

## How To Use

You can read a quick overview of the tool and its functionality [here](https://blog.yagasoft.com/2020/09/dynamics-template-based-code-generator-supercharged).

To get started, install the Visual Studio extension ([here](https://marketplace.visualstudio.com/items?itemName=Yagasoft.CrmCodeGenerator)).

Note: any window can be closed by pressing the _ESC_ button on the keyboard, even if the generator is busy.

#### Add a template to your project

Highlight the project where you want to add the template and generated code.   
Click on Tools –> Add CRM Code Generator Template... (if you don't see this menu, then shutdown VS and reinstall the extension).

![File](https://github.com/yagasoft/DynamicsCrm-CodeGenerator/raw/master/guide/images/crm-generator-external-06.png)

  + Start with one of the provided templates.
  + After a template is added to your project you will be prompted for CRM connection info.
  + Pick the entities that you want to include.
  + Click the "Generate Code" button.

If you make schema changes in CRM and you want to refresh the code, right click the template and select "Run Custom Tool".

![File](https://github.com/yagasoft/DynamicsCrm-CodeGenerator/raw/master/guide/images/crm-generator-external-07.png)

#### Changing the template

When you make changes to the template and save, Visual Studio will automatically attempt to regenerate the code.

## Screenshots

![File](https://github.com/yagasoft/DynamicsCrm-CodeGenerator/raw/master/guide/images/crm-generator-external-01.png)

![File](https://github.com/yagasoft/DynamicsCrm-CodeGenerator/raw/master/guide/images/crm-generator-external-02.png)

![File](https://github.com/yagasoft/DynamicsCrm-CodeGenerator/raw/master/guide/images/crm-generator-external-03.png)

![File](https://github.com/yagasoft/DynamicsCrm-CodeGenerator/raw/master/guide/images/crm-generator-external-04.png)

![File](https://github.com/yagasoft/DynamicsCrm-CodeGenerator/raw/master/guide/images/crm-generator-external-05.png)

## Upcoming/planned

+ Add: Visual Studio Shared Projects support
+ Add: undo/redo
+ Add: parse placeholders in annotations for LogicalName and variable name
+ Add: [template] File field, with a Get and Set that uses the SDK message
+ Add: enum annotations (DisplayName ... etc.)
+ Add: option to add alternate keys to contracts
+ Add: option to use CRM-only contracts to replace Contract classes, optionally
+ Add: [template] an attribute/annotation to the Clear Flag fields in contracts, to ease parsing them in helper methods
+ Add: [template] XrmDefinitelyTyped support, and generate form structure
+ Improve: [template] rework lookup labels localisation
  + After the upgrade to v7, it has been buggy, and I don't like how it uses ExecuteMultiple to load labels in the first place; so I need to come up with a method that is faster but still as efficient
+ Fix: [template] helpers to support new stuff since v7
  + LoadRelation methods

## Credits & Contributions

+ [Eric Labashosky](https://github.com/xairrick):
  + Original extension base code
  + My work:
    + Redesigned the screens and most of the logic
    + Greatly boosted the generation and regeneration speed
    + Added the features that don't exist in the Microsoft's tool
+ Ramy Victor:
  + Enhancements
  + Debugging during the early versions
+ Mohammed Ghoname:
  + New feature suggestions during the early versions
+ [ClemensWon](https://github.com/ClemensWon):
  + Global option-sets

## Changes
+ Check Releases page for the later changes
#### _v1.1.1 (2015-03-01)_
+ Initial release

---
**Copyright &copy; by Ahmed Elsawalhy ([Yagasoft](https://yagasoft.com))** -- _GPL v3 Licence_
