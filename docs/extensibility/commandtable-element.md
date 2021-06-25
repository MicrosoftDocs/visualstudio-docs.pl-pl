---
title: CommandTable, element | Microsoft Docs
description: CommandTable jest elementem głównym pliku vsct, który definiuje układ i typ poleceń, które pakiet VSPackage dostarcza do środowiska IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 55faf4ee8bdc7ec261508fd07f5a573e7a29560f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901854"
---
# <a name="commandtable-element"></a>CommandTable, element
CommandTable jest elementem głównym pliku *vsct.* Jest to plik, który definiuje rzeczywisty układ i typ poleceń, które pakiet VSPackage dostarcza do środowiska IDE. Polecenia mogą zawierać elementy menu, menu, paski narzędzi i pola kombi. Aby uzyskać więcej informacji, [zobacz Visual Studio tabeli poleceń (vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

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
| Xmlns | Wymagane. Przestrzenie nazw XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs=" <http://www.w3.org/2001/XMLSchema> " |
| language | Opcjonalny. Atrybut języka może służyć do określania domyślnego języka wszystkich \<Strings> elementów w tabeli poleceń.  Jeśli język nie zostanie określony, zostanie użyty język bieżącego procesu:<br /><br /> language="en-us" |

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Extern, element](../extensibility/extern-element.md)|Opcjonalny. Zawiera dyrektywy preprocesora dla kompilatora.|
|[Include, element](../extensibility/include-element.md)|Opcjonalny. Zawiera ścieżki do wszystkich plików do dołączyć do kompilacji.|
|[Define, element](../extensibility/define-element.md)|Opcjonalny. Definiuje symbol na jego nazwę i wartość.|
|[Commands, element](../extensibility/commands-element.md)|Opcjonalny. Element nadrzędny definiujący wszystkie polecenia dla elementu VSPackage, który zawiera wszystkie inne elementy.|
|[CommandPlacements, element](../extensibility/commandplacements-element.md)|Opcjonalny. Określa, gdzie na pasku poleceń mają być umieszczone polecenia.|
|[VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)|Opcjonalny. Określa statyczną widoczność poleceń i pasków narzędzi.|
|[KeyBindings, element](../extensibility/keybindings-element.md)|Opcjonalny. Określa kombinacje klawiszy skrótów, jeśli są dostępne, dla poleceń.|
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Opcjonalny. Umożliwia pakietowi VSPackage opcjonalne zaimplementowanie własnej wersji funkcji, która pierwotnie była obsługiwana przez inne pakiet VSPackage.|
|[Symbols, element](https://www.microsoft.com/download/details.aspx?id=55984)|Opcjonalny. Zawiera wszystkie dane symboli — identyfikatory GUID, identyfikatory itd. — dla kompilatora.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|Brak||

## <a name="see-also"></a>Zobacz też
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
