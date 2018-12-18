---
title: CommandPlacement, Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53a60949cdda6d026525dcc8be5bab8f82a0fb73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741544"
---
# <a name="commandplacement-element"></a>CommandPlacement, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandPlacement, element umożliwia przyciski, grup i menu, mają zostać uwzględnione w więcej niż jednej grupie lub menu. Przy użyciu elementu CommandPlacement, nie trzeba całkowicie ponownie zdefiniować te elementy, aby zmodyfikować wygląd interfejsu użytkownika.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenia wielokrotnego użytku, do grup przycisków](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagana. Identyfikator guid zestawu poleceń, zgodnie z definicją w [Symbols, Element](../extensibility/symbols-element.md).|  
|identyfikator|Wymagana. Identyfikator menu, grupy lub polecenie, aby umieścić zgodnie z definicją w `Symbols Element`.|  
|priorytet|Wymagana. Określa położenie visual elementu w jego elementu nadrzędnego.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Wymagana. Menu lub grupy, która hostuje element które mają być umieszczone.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandPlacements, element](../extensibility/commandplacements-element.md)|Określa grupy CommandPlacements i CommandPlacement elementów.|  
  
## <a name="example"></a>Przykład  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [CommandPlacements, Element](../extensibility/commandplacements-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

