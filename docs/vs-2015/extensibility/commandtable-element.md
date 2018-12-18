---
title: CommandTable, Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1adc3e8f8c7894cfb3a55617ce594f52a60f2498
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817376"
---
# <a name="commandtable-element"></a>CommandTable, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable jest głównym elementem pliku vsct. Jest to plik który definiuje układ i typ poleceń, udostępnianych przez pakietu VSPackage środowiska IDE. Polecenia może zawierać elementy menu, menu, paski narzędzi i pola kombi. Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|   xmlns   |                                   Wymagana. Obszary nazw XML:<br /><br /> xmlns = "<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:xs = "<http://www.w3.org/2001/XMLSchema>"                                   |
| język  | Opcjonalna. Atrybut language może służyć do określania domyślny język wszystkich \<ciągi > elementów w tabeli poleceń.  Jeśli język nie zostanie określony, będzie używany język bieżącego procesu:<br /><br /> Language = "en-us" |
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Extern, element](../extensibility/extern-element.md)|Opcjonalna. Zawiera dyrektywy preprocesora dla kompilatora.|  
|[Include, element](../extensibility/include-element.md)|Opcjonalna. Zawiera ścieżki do plików do uwzględnienia w kompilacji.|  
|[Define, element](../extensibility/define-element.md)|Opcjonalna. Definiuje symbol, biorąc pod uwagę jego nazwy i wartości.|  
|[Commands, element](../extensibility/commands-element.md)|Opcjonalna. Element nadrzędny definiujący wszystkie polecenia dla pakietu VSPackage, który zawiera wszystkie inne elementy.|  
|[CommandPlacements, element](../extensibility/commandplacements-element.md)|Opcjonalna. Określa, gdzie na pasku poleceń, polecenia zostaną umieszczone.|  
|[VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)|Opcjonalna. Określa statyczne widoczności poleceń i paski narzędzi.|  
|[KeyBindings, element](../extensibility/keybindings-element.md)|Opcjonalna. Określa kombinacji klawiszy skrótów dla polecenia.|  
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Opcjonalna. Umożliwia opcjonalnie zaimplementować własną wersję funkcji początkowo obsługiwana przez innych pakietów VSPackage pakietu VSPackage.|  
|[Symbols, element](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Opcjonalna. Zawiera wszystkie dane symboliczne — identyfikatory GUID, identyfikatory itd. — dla kompilatora.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

