---
title: Element CommandTable | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739649"
---
# <a name="commandtable-element"></a>Element CommandTable
CommandTable jest głównym elementem pliku *vsct.* Jest to plik, który definiuje rzeczywisty układ i typ poleceń, które VSPackage zapewnia IDE. Polecenia mogą zawierać elementy menu, menu, paski narzędzi i pola kombi. Aby uzyskać więcej informacji, zobacz [Pliki tabeli poleceń programu Visual Studio (vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

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
| Xmlns | Wymagany. Przestrzenie nazw XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| language | Element opcjonalny. Atrybut języka może służyć do określenia domyślnego \<języka wszystkich ciągów> elementów w tabeli poleceń.  Jeśli język nie zostanie określony, język bieżącego procesu będzie używany:<br /><br /> language="en-us" |

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element Extern](../extensibility/extern-element.md)|Element opcjonalny. Zawiera dyrektywy preprocesora dla kompilatora.|
|[Dołącz element](../extensibility/include-element.md)|Element opcjonalny. Zawiera ścieżki do wszystkich plików do uwzględnienia w kompilacji.|
|[Zdefiniuj element](../extensibility/define-element.md)|Element opcjonalny. Definiuje symbol, biorąc pod uwagę jego nazwę i wartość.|
|[Element Polecenia](../extensibility/commands-element.md)|Element opcjonalny. Element nadrzędny definiujący wszystkie polecenia dla VSPackage, który zawiera wszystkie inne elementy.|
|[Element Połowisku](../extensibility/commandplacements-element.md)|Element opcjonalny. Określa, gdzie na pasku poleceń mają być umieszczone polecenia.|
|[Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Element opcjonalny. Określa statyczną widoczność poleceń i pasków narzędzi.|
|[Element KeyBindings](../extensibility/keybindings-element.md)|Element opcjonalny. Określa kombinacje klawiszy skrótów, jeśli istnieją, dla poleceń.|
|[Element UsedCommands](../extensibility/usedcommands-element.md)|Element opcjonalny. Umożliwia VSPackage opcjonalnie zaimplementować własną wersję funkcji pierwotnie obsługiwane przez inne vspackages.|
|[Symbole, element](https://www.microsoft.com/download/details.aspx?id=55984)|Element opcjonalny. Zawiera wszystkie dane symbolu — identyfikatory GUID, identyfikatory itd i tak dalej — dla kompilatora.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|Brak||

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
