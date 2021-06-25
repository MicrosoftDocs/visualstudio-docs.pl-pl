---
title: Button, element | Microsoft Docs
description: 'Element Button definiuje element, z który użytkownik może wchodzić w interakcje. Przyciski mogą być różnego rodzaju: Button, MenuButton i SplitDropDown.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 630d848c40b13a929c3dd91b47e1c35529efaa50
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901750"
---
# <a name="button-element"></a>Button, element
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
|guid|Wymagane. Identyfikator GUID/ID identyfikatora polecenia.|
|identyfikator|Wymagane. Identyfikator identyfikatora GUID/ID polecenia.|
|priority|Opcjonalny. Wartość liczbowa określająca priorytet.|
|typ|Opcjonalny. Wyliczeniowa wartość określająca rodzaj przycisku.<br /><br /> Jeśli nie zostanie podana, użyje przycisku.<br /><br /> Przycisk<br /> Standardowe polecenie, które jest wyświetlane na paskach narzędzi (zazwyczaj jako przycisk ikony), menu i menu kontekstowych.<br /><br /> MenuButton<br /> Element menu, który nie wykonuje polecenia, ale tworzy inne menu.<br /><br /> SplitDropDown<br /> Kontrolki, takie jak przyciski Cofnij i Ponownie wywłaszczaj na standardowym pasku narzędzi w programie Microsoft Word.|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element nadrzędny](../extensibility/parent-element.md)|Opcjonalny. Element nadrzędny przycisku.|
|[Icon, element](../extensibility/icon-element.md)|Opcjonalny. Ikona skojarzona z przyciskiem .|
|[Element flagi polecenia](../extensibility/command-flag-element.md)|Wymagane. Prawidłowe wartości CommandFlag przycisku są następujące.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility (DynamicVisibility)<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> — Pict<br /><br /> — PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges (Zmiany tekstu)<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly (Tylko tekst)|
|[Strings, element](../extensibility/strings-element.md)|Wymagane. Należy zdefiniować [podrzędny element ButtonText.](../extensibility/buttontext-element.md)|
|Adnotacja|Opcjonalny komentarz.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Buttons, element](../extensibility/buttons-element.md)|Grupuj elementy przycisku.|

## <a name="example"></a>Przykład
 W poniższym przykładzie zdefiniowano przycisk w *pliku vsct.*

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
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
