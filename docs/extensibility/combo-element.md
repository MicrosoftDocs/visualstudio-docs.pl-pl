---
title: Combo, element | Microsoft Docs
description: 'Combo element definiuje polecenia, które pojawiają się w polu kombi. Istnieją cztery rodzaje: DropDownCombo, DynamicCombo, IndexCombo i MRUCombo.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 431d68b6e545506f5fc90cc5a98a52dd4f1c33ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904958"
---
# <a name="combo-element"></a>Combo, element
Definiuje polecenia wyświetlane w polu kombi. Istnieją cztery rodzaje pól kombi w następujący sposób: DropDownCombo, DynamicCombo, IndexCombo i MRUCombo.

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
|guid|Wymagane. Identyfikator GUID/ID identyfikatora polecenia.|
|identyfikator|Wymagane. Identyfikator identyfikatora GUID/ID polecenia.|
|defaultWidth|Wymagane. Liczba całkowita określająca szerokość pikseli dla pola kombi.|
|idCommandList|Wymagane. Identyfikator wysyłany do aktywnego obiektu docelowego polecenia w celu pobrania listy elementów do wyświetlania w polu kombi. Identyfikator będzie w tym samym zakresie identyfikatora GUID co kontrolka.|
|priority|Opcjonalny. Wartość liczbowa określająca priorytet.|
|typ|Opcjonalny. Wyliczeniowa wartość określająca typ przycisku.<br /><br /> Jeśli nie zostanie podany, użyj przycisku.<br /><br /> DropDownCombo<br /> Pakiet VSPackage jest odpowiedzialny za wypełnienie zawartości tego pola kombi. Użytkownik nie może wpisać niczego w polu tekstowym tej listy rozwijanej.<br /><br /> DynamicCombo<br /> Pakiet VSPackage jest odpowiedzialny za wypełnienie zawartości tego pola kombi. Użytkownik może edytować to kombi, a także wybierać w nim elementy.<br /><br /> IndexCombo<br /> Taki sam jak DynamicCombo, z tą różnicą, że wywołuje indeks elementu, a nie jego tekst.<br /><br /> MRUCombo<br /> Wypełnione przez zintegrowane środowisko projektowe (IDE) w imieniu vspackage.  Użytkownik może edytować w tym polu kombi. Ide zapamiętuje maksymalnie 16 ostatnich wpisów na pole kombi.<br /><br /> Gdy użytkownik wybierze coś w polu kombi lub wprowadzi coś nowego, idee powiadomią odpowiedni pakiet VSPackage.|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny|Opcjonalny. Element nadrzędny przycisku.|
|CommandFlag|Wymagane. Zobacz [element flagi polecenia](../extensibility/command-flag-element.md). Prawidłowe wartości CommandFlag przycisku są następujące.<br /><br /> — Bez uwzględniania przypadku<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility (DynamicVisibility)<br /><br /> - FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> — Nie dojrzej<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Ciągi|Wymagane. Zobacz [ciągi, element](../extensibility/strings-element.md). Należy zdefiniować podrzędny element ButtonText.|
|Adnotacja|Opcjonalny komentarz.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Commands, element](../extensibility/commands-element.md)|Reprezentuje kolekcję poleceń na pasku narzędzi vsPackage.|

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

## <a name="see-also"></a>Zobacz także
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
