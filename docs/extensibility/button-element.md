---
title: Element przycisku | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739930"
---
# <a name="button-element"></a>Element przycisku
Definiuje element, z który użytkownik może wchodzić w interakcje. Przyciski mogą być różnego rodzaju: Button, MenuButton i SplitDropDown.

## <a name="syntax"></a>Składnia

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|
|id|Wymagany. Identyfikator polecenia GUID/ID.|
|priority|Element opcjonalny. Wartość liczbowa określająca priorytet.|
|type|Element opcjonalny. Wyliczona wartość określająca rodzaj przycisku.<br /><br /> Jeśli nie podano, używa buttona.<br /><br /> Button<br /> Standardowe polecenie wyświetlane na paskach narzędzi (zazwyczaj jako przycisk ikony), menu i menu kontekstowe.<br /><br /> MenuButton<br /> Element menu, który nie wykonuje polecenia, ale tworzy inne menu.<br /><br /> SplitDropDown (SplitDropDown)<br /> Formanty, takie jak przyciski Cofnij i Ponawij na standardowym pasku narzędzi w programie Microsoft Word.|
|Warunek|Element opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element nadrzędny](../extensibility/parent-element.md)|Element opcjonalny. Element nadrzędny przycisku.|
|[Element ikony](../extensibility/icon-element.md)|Element opcjonalny. Ikona skojarzona z przyciskiem.|
|[Element flagi polecenia](../extensibility/command-flag-element.md)|Wymagany. Prawidłowe commandflag wartości dla Button są następujące.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - Dynamiczna niewidzialność<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> - Pict<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - Zmiany tekstu<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly|
|[Element ciągów](../extensibility/strings-element.md)|Wymagany. Element [podrzędny ButtonText](../extensibility/buttontext-element.md) musi być zdefiniowany.|
|Adnotacja|Opcjonalny komentarz.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element przycisków](../extensibility/buttons-element.md)|Elementy przycisku Grupy.|

## <a name="example"></a>Przykład
 Poniższy przykład definiuje przycisk w pliku *vsct.*

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
