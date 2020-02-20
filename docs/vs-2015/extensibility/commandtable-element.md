---
title: Element polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb2b874f7bbe94e383e9e7fba755dcc373a93150
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477047"
---
# <a name="commandtable-element"></a>CommandTable, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Polecenie jest głównym elementem pliku. vsct. Jest to plik, który definiuje rzeczywisty układ i typ poleceń, które pakietu VSPackage zapewnia IDE. Polecenia mogą obejmować elementy menu, menu, paski narzędzi i pola kombi. Aby uzyskać więcej informacji, zobacz [tabela poleceń programu Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
| Atrybut |                                                                                                                   Opis                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Wymagany. Przestrzenie nazw XML:<br /><br /> `xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"`<br /><br /> `xmlns:xs="<http://www.w3.org/2001/XMLSchema>"`                                   |
| language  | Opcjonalny. Atrybut Language może służyć do określania domyślnego języka wszystkich \<ciągów > elementów w tabeli poleceń.  Jeśli język nie zostanie określony, będzie używany język bieżącego procesu:<br /><br /> Language = "pl-US" |
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Extern, element](../extensibility/extern-element.md)|Opcjonalny. Zawiera dyrektywy preprocesora dla kompilatora.|  
|[Include, element](../extensibility/include-element.md)|Opcjonalny. Zawiera ścieżki do dowolnych plików do uwzględnienia w kompilacji.|  
|[Define, element](../extensibility/define-element.md)|Opcjonalny. Definiuje symbol o nazwie i wartości.|  
|[Commands, element](../extensibility/commands-element.md)|Opcjonalny. Element nadrzędny definiujący wszystkie polecenia dla pakietu VSPackage, które zawierają wszystkie pozostałe elementy.|  
|[CommandPlacements, element](../extensibility/commandplacements-element.md)|Opcjonalny. Definiuje, gdzie na pasku poleceń mają być umieszczane polecenia.|  
|[VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)|Opcjonalny. Określa statyczną widoczność poleceń i pasków narzędzi.|  
|[KeyBindings, element](../extensibility/keybindings-element.md)|Opcjonalny. Określa kombinacje klawiszy skrótu (jeśli istnieją) dla poleceń.|  
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Opcjonalny. Zezwala pakietu VSPackage na opcjonalnie zaimplementować własną wersję funkcji oryginalnie obsługiwaną przez inne pakietów VSPackage.|  
|[Symbols, element](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Opcjonalny. Zawiera dowolne dane symboli--identyfikatory GUID, identyfikatory i tak dalej — dla kompilatora.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|None||  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
