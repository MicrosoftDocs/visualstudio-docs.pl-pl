---
title: Typy elementów modelu UML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, types
ms.assetid: 25345a53-7246-4eb7-8ad9-0b695aa171a2
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 55311d02bef9654637a1b413519cc562a5c7f52b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758533"
---
# <a name="uml-model-element-types"></a>Typy elementów modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Może odczytywać i modyfikować modelu UML za pośrednictwem interfejsu programowania. Ten temat zawiera podsumowanie hierarchii typów elementów. Hierarchia jest taka sama jak zdefiniowana w specyfikacji UML.  
  
 Szczegółowe informacje o poszczególnych typów znajdują się w [wykaz interfejsów API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  
  
## <a name="element-types"></a>Typy elementów  
 Jest to zbiór typów zdefiniowanych w zestawie `Microsoft.VisualStudio.Uml.Interfaces.dll`.  
  
 W pełni kwalifikowana nazwa każdego elementu to "`Microsoft.VisualStudio.Uml.`" następuje nazwa na liście.  
  
 Dla wygody ta lista jest określony jako hierarchię dziedziczenia. W przypadku, gdy typ ma więcej niż jeden nadtypu, nadtypów dodatkowe są wyświetlane po dwukropek (:).  
  
```  
  
Classes.IElement  
|  Activities.IActivityGroup  
|  Classes.IComment  
|  Classes.IMultiplicityElement  
|  |  CompositeStructures.IConnectorEnd  
|  Classes.INamedElement  
|  |  Deployments.IDeployedArtifact  
|  |  Deployments.IDeploymentTarget  
|  |  |  Classes.IInstanceSpecification  
             : Deployments.IDeployedArtifact,  
               Deployments.IDeploymentTarget  
|  |  |  |  Classes.IEnumerationLiteral  
|  |  Interactions.IInteractionFragment  
|  |  |  Interactions.ICombinedFragment  
|  |  |  |  Interactions.IConsiderIgnoreFragment  
|  |  |  Interactions.IExecutionSpecification  
|  |  |  |  Interactions.IActionExecutionSpecification  
|  |  |  |  Interactions.IBehaviorExecutionSpecification  
|  |  |  Interactions.IInteraction  : CommonBehaviors.IBehavior  
|  |  |  Interactions.IInteractionOperand : Classes.INamespace  
|  |  |  Interactions.IInteractionUse  
|  |  |  Interactions.IOccurrenceSpecification  
|  |  |  |  Interactions.IExecutionOccurrenceSpecification  
|  |  |  |  Interactions.IMessageOccurrenceSpecification  
                   : Interactions.IMessageEnd  
|  |  |  |  |  Interactions.ILostFoundTarget  
|  |  |  |  Interactions.IOperandOccurrenceSpecification  
|  |  |  Interactions.IStateInvariant  
|  |  Interactions.ILifeline  
|  |  Interactions.IMessage  
|  |  Interactions.IMessageEnd  
|  |  Classes.INamespace  
|  |  |  Classes.IPackage  
             : Classes.IPackageableElement,  
              AuxiliaryConstructs.ITemplateableElement  
|  |  |  |  AuxiliaryConstructs.IModel  
|  |  |  Activities.IState  
|  |  Classes.IPackageableElement        
                   : AuxiliaryConstructs.IParameterableElement  
|  |  |  Classes.IConstraint  
|  |  |  |  Interactions.IInteractionConstraint  
|  |  |  CommonBehaviors.IEvent  
|  |  |  |  Interactions.IExecutionEvent  
|  |  |  |  CommonBehaviors.IMessageEvent  
|  |  |  |  |  CommonBehaviors.ICallEvent  
|  |  |  |  |  Interactions.IReceiveOperationEvent  
|  |  |  |  |  Interactions.IReceiveSignalEvent  
|  |  |  |  |  Interactions.ISendOperationEvent  
|  |  |  |  |  Interactions.ISendSignalEvent  
|  |  |  Classes.IType  
|  |  |  |  Classes.IClassifier : Classes.INamespace, Classes.IRedefinableElement, AuxiliaryConstructs.ITemplateableElement  
|  |  |  |  |  Deployments.IArtifact  
                   : Deployments.IDeployedArtifact  
|  |  |  |  |  |  Deployments.IDeploymentSpecification  
|  |  |  |  |  CommonBehaviors.IBehavioredClassifier  
|  |  |  |  |  |  UseCases.IActor  
|  |  |  |  |  |  Classes.IClass        
                         : CompositeStructures.IEncapsulatedClassifier  
|  |  |  |  |  |  |  CommonBehaviors.IBehavior  
|  |  |  |  |  |  |  |  Activities.IActivity  
|  |  |  |  |  |  |  Components.IComponent  
|  |  |  |  |  |  |  |  UseCases.ISubsystem  
|  |  |  |  |  |  |  Deployments.INode : IDeploymentTarget  
|  |  |  |  |  |  |  |  Deployments.IDevice  
|  |  |  |  |  |  |  |  Deployments.IExecutionEnvironment  
|  |  |  |  |  |  UseCases.IUseCase  
|  |  |  |  |  Classes.IDataType  
|  |  |  |  |  |  Classes.IEnumeration  
|  |  |  |  |  |  Classes.IPrimitiveType  
|  |  |  |  |  Classes.IInterface  
|  |  |  |  |  CompositeStructures.IStructuredClassifier  
|  |  |  |  |  |  CompositeStructures.IEncapsulatedClassifier  
|  |  |  Classes.IValueSpecification : Classes.ITypedElement  
|  |  |  |  Classes.IExpression  
|  |  |  |  Classes.IInstanceValue  
|  |  |  |  Classes.ILiteralSpecification  
|  |  |  |  |  Classes.ILiteralBoolean  
|  |  |  |  |  Classes.ILiteralInteger  
|  |  |  |  |  Classes.ILiteralNull  
|  |  |  |  |  Classes.ILiteralString  
|  |  |  |  |  Classes.ILiteralUnlimitedNatural  
|  |  |  |  Classes.IOpaqueExpression  
|  |  Classes.IRedefinableElement  
|  |  |  Activities.IActivityNode  
|  |  |  |  Activities.IControlNode  
|  |  |  |  |  Activities.IDecisionNode  
|  |  |  |  |  Activities.IFinalNode  
|  |  |  |  |  |  Activities.IActivityFinalNode  
|  |  |  |  |  Activities.IForkNode  
|  |  |  |  |  Activities.IInitialNode  
|  |  |  |  |  Activities.IJoinNode  
|  |  |  |  |  Activities.IMergeNode  
|  |  |  |  Activities.IExecutableNode  
|  |  |  |  |  Actions.IAction  
|  |  |  |  |  |  Actions.IAcceptEventAction  
|  |  |  |  |  |  Actions.ICreateObjectAction  
|  |  |  |  |  |  Actions.IInvocationAction  
|  |  |  |  |  |  |  Actions.ICallAction  
|  |  |  |  |  |  |  |  Actions.ICallBehaviorAction  
|  |  |  |  |  |  |  |  Actions.ICallOperationAction  
|  |  |  |  |  |  |  Actions.ISendSignalAction  
|  |  |  |  |  |  Actions.IOpaqueAction  
|  |  |  |  Activities.IObjectNode  : Classes.ITypedElement  
|  |  |  |  |  Activities.IActivityParameterNode  
|  |  |  |  |  Actions.IPin : Classes.IMultiplicityElement  
|  |  |  |  |  |  Actions.IInputPin  
|  |  |  |  |  |  Actions.IOutputPin  
|  |  |  UseCases.IExtensionPoint  
|  |  |  Classes.IFeature  
|  |  |  |  Classes.IBehavioralFeature  : Classes.INamespace  
|  |  |  |  |  Classes.IOperation  
                   : AuxiliaryConstructs.ITemplateableElement,  
                   AuxiliaryConstructs.IParameterableElement  
|  |  |  |  Classes.IStructuralFeature  
              : Classes.IMultiplicityElement,   
                Classes.ITypedElement  
|  |  |  |  |  Classes.IProperty  
                   : AuxiliaryConstructs.ITemplateableElement,   
                   CompositeStructures.IConnectableElement,   
                   Deployments.IDeploymentTarget  
|  |  |  |  |  |  CompositeStructures.IPort  
|  |  Classes.ITypedElement  
|  |  |  CompositeStructures.IConnectableElement  
             : AuxiliaryConstructs.IParameterableElement  
|  |  |  Classes.IParameter  : Classes.IMultiplicityElement, CompositeStructures.IConnectableElement  
|  AuxiliaryConstructs.IParameterableElement  
|  Classes.IProfileInstance  
  
|  Classes.IRelationship  
|  |  Activities.IActivityEdge : Classes.IRedefinableElement  
|  |  |  Activities.IControlFlow  
|  |  |  Activities.IObjectFlow  
|  |  Classes.IAssociation : IClassifier  
|  |  |  Deployments.ICommunicationPath  
|  |  CompositeStructures.IConnector  
|  |  Classes.IDirectedRelationship  
|  |  |  Classes.IDependency : Classes.IPackageableElement  
|  |  |  |  Classes.IAbstraction  
|  |  |  |  |  Deployments.IManifestation  
|  |  |  |  |  Classes.IRealization  
|  |  |  |  |  |  Classes.IInterfaceRealization  
|  |  |  |  Deployments.IDeployment  
|  |  |  |  Classes.IUsage  
|  |  |  UseCases.IExtend : Classes.INamedElement  
|  |  |  Classes.IGeneralization  
|  |  |  UseCases.IInclude : Classes.INamedElement  
|  |  |  Classes.IPackageImport  
|  |  |  AuxiliaryConstructs.ITemplateBinding  
|  Classes.IStereotypeInstance  
|  Classes.IStereotypePropertyInstance  
|  AuxiliaryConstructs.ITemplateableElement  
|  AuxiliaryConstructs.ITemplateParameter  
|  |  AuxiliaryConstructs.IClassifierTemplateParameter  
|  |  AuxiliaryConstructs.IOperationTemplateParameter  
|  AuxiliaryConstructs.ITemplateParameterSubstitution  
|  AuxiliaryConstructs.ITemplateSignature  
|  |  AuxiliaryConstructs.IRedefinableTemplateSignature   
             : Classes.IRedefinableElement  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie profilu w celu rozszerzenia UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Wykaz interfejsów API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md)



