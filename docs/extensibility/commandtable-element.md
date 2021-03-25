---
title: Element polecenia | Microsoft Docs
description: Polecenie jest głównym elementem pliku vsct, który definiuje układ i typ poleceń dostarczanych przez pakietu VSPackage do IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 507bdd20602c680f58b62e85251eaaa592982bc7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089527"
---
# <a name="commandtable-element"></a>Element polecenia
Polecenie jest głównym elementem pliku *. vsct* . Jest to plik, który definiuje rzeczywisty układ i typ poleceń, które pakietu VSPackage zapewnia IDE. Polecenia mogą obejmować elementy menu, menu, paski narzędzi i pola kombi. Aby uzyskać więcej informacji, zobacz [pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

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

| Atrybut | Opis |
|-----------| - |
| 'xmlns | Wymagane. Przestrzenie nazw XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = " <http://www.w3.org/2001/XMLSchema> " |
| language | Opcjonalny. Atrybut Language może służyć do określania języka domyślnego wszystkich \<Strings> elementów w tabeli poleceń.  Jeśli język nie zostanie określony, będzie używany język bieżącego procesu:<br /><br /> Language = "pl-US" |

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element extern](../extensibility/extern-element.md)|Opcjonalny. Zawiera dyrektywy preprocesora dla kompilatora.|
|[Include — element](../extensibility/include-element.md)|Opcjonalny. Zawiera ścieżki do dowolnych plików do uwzględnienia w kompilacji.|
|[Zdefiniuj element](../extensibility/define-element.md)|Opcjonalny. Definiuje symbol o nazwie i wartości.|
|[Commands, element](../extensibility/commands-element.md)|Opcjonalny. Element nadrzędny definiujący wszystkie polecenia dla pakietu VSPackage, które zawierają wszystkie pozostałe elementy.|
|[CommandPlacements, element](../extensibility/commandplacements-element.md)|Opcjonalny. Definiuje, gdzie na pasku poleceń mają być umieszczane polecenia.|
|[VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)|Opcjonalny. Określa statyczną widoczność poleceń i pasków narzędzi.|
|[Element powiązań klawiszy](../extensibility/keybindings-element.md)|Opcjonalny. Określa kombinacje klawiszy skrótu (jeśli istnieją) dla poleceń.|
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Opcjonalny. Zezwala pakietu VSPackage na opcjonalnie zaimplementować własną wersję funkcji oryginalnie obsługiwaną przez inne pakietów VSPackage.|
|[Symbol — element](https://www.microsoft.com/download/details.aspx?id=55984)|Opcjonalny. Zawiera dowolne dane symboli--identyfikatory GUID, identyfikatory i tak dalej — dla kompilatora.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|Brak||

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
