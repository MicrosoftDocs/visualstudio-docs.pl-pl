---
title: Element kombi | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739819"
---
# <a name="combo-element"></a>Element kombi
Definiuje polecenia wyświetlane w polu kombi. Istnieją cztery rodzaje pól kombi, w następujący sposób: DropDownCombo, DynamicCombo, IndexCombo i MRUCombo.

## <a name="syntax"></a>Składnia

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|
|id|Wymagany. Identyfikator polecenia GUID/ID.|
|defaultWidth|Wymagany. Liczba całkowita określająca szerokość piksela dla pola kombi.|
|idCommandList|Wymagany. Identyfikator, który jest wysyłany do aktywnego obiektu docelowego polecenia w celu pobrania listy elementów, które mają być wyświetlane w polu kombi. Identyfikator będzie w tym samym zakresie GUID jako formant.|
|priority|Element opcjonalny. Wartość liczbowa określająca priorytet.|
|type|Element opcjonalny. Wyliczona wartość określająca typ przycisku.<br /><br /> Jeśli nie podano, używa buttona.<br /><br /> RozwijaneCombo<br /> VSPackage jest odpowiedzialny za wypełnienie zawartości dla tego pola kombi. Użytkownik nie może wpisać niczego w polu tekstowym tej listy rozwijanej.<br /><br /> DynamicCombo (DynamiczneCombo)<br /> VSPackage jest odpowiedzialny za wypełnienie zawartości tego pola kombi. Użytkownik może edytować to kombi, a także wybrać elementy w nim.<br /><br /> IndeksCombo<br /> Tak samo jak DynamicCombo z tą różnicą, że podnosi indeks elementu, a nie jego tekst.<br /><br /> MRUCombo (MruCombo)<br /> Wypełnione przez zintegrowane środowisko programistyczne (IDE) w imieniu VSPackage.  Użytkownik może edytować w tym polu kombi. IDE zapamiętuje do ostatnich 16 wpisów na pole kombi.<br /><br /> Gdy użytkownik wybierze coś w polu kombi lub wprowadzi coś nowego, IDE powiadamia odpowiednie VSPackage.|
|Warunek|Element opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny|Element opcjonalny. Element nadrzędny przycisku.|
|CommandFlag (Żużel dowodzenia)|Wymagany. Zobacz [Element flagi polecenia](../extensibility/command-flag-element.md). Prawidłowe commandflag wartości dla Button są następujące.<br /><br /> - CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - Dynamiczna niewidzialność<br /><br /> - Klawisze filtracyjne<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - RozciągnięcieHorizontally|
|Ciągi|Wymagany. Zobacz [Strings element](../extensibility/strings-element.md). Element podrzędny ButtonText musi być zdefiniowany.|
|Adnotacja|Opcjonalny komentarz.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element Polecenia](../extensibility/commands-element.md)|Reprezentuje kolekcję poleceń na pasku narzędzi VSPackage.|

## <a name="example"></a>Przykład

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
