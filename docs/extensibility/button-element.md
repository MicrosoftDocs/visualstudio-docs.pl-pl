---
title: Button — element | Microsoft Docs
description: 'Element Button definiuje element, z którym użytkownik może korzystać. Przyciski mogą być różnego rodzaju: Button, MenuButton i SplitDropDown.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 51b202db9210fa5c1f3d5b26b5177cc0b5e1e0a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927317"
---
# <a name="button-element"></a>Button — element
Definiuje element, z którym użytkownik może korzystać. Przyciski mogą być różnego rodzaju: Button, MenuButton i SplitDropDown.

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
|guid|Wymagane. Identyfikator GUID identyfikatora polecenia GUID/ID.|
|identyfikator|Wymagane. Identyfikator identyfikatora polecenia GUID/ID.|
|priority|Opcjonalny. Wartość liczbowa, która określa priorytet.|
|typ|Opcjonalny. Wartość wyliczana, która określa rodzaj przycisku.<br /><br /> Jeśli nie zostanie określona, używa przycisku.<br /><br /> Przycisk<br /> Standardowe polecenie, które pojawia się na paskach narzędzi (zazwyczaj jako przycisk ikony), menu i menu kontekstowe.<br /><br /> MenuButton<br /> Element menu, który nie wykonuje polecenia, ale tworzy inne menu.<br /><br /> SplitDropDown<br /> Kontrolki, takie jak przyciski Cofnij i wykonaj ponownie na standardowym pasku narzędzi w programie Microsoft Word.|
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element nadrzędny](../extensibility/parent-element.md)|Opcjonalny. Element nadrzędny przycisku.|
|[Icon — element](../extensibility/icon-element.md)|Opcjonalny. Ikona skojarzona z przyciskiem.|
|[Element flagi polecenia](../extensibility/command-flag-element.md)|Wymagane. Prawidłowe wartości CommandFlag dla przycisku są następujące.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> -Nodostosowywanie<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> — PICT<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> -TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> -TextOnly|
|[Strings, element](../extensibility/strings-element.md)|Wymagane. Element podrzędny [ButtonText](../extensibility/buttontext-element.md) musi być zdefiniowany.|
|Adnotacja|Opcjonalny komentarz.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element Buttons](../extensibility/buttons-element.md)|Elementy przycisków grup.|

## <a name="example"></a>Przykład
 Poniższy przykład definiuje przycisk w pliku *. vsct* .

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
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
