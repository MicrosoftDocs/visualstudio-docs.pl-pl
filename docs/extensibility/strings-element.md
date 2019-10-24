---
title: String — element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c91a8ea07daee77855017d641a569a892612c3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719441"
---
# <a name="strings-element"></a>Strings, element
Element Strings musi zawierać co najmniej element podrzędny **ButtonText** . Wszystkie inne elementy podrzędne są opcjonalne. Nieprawidłowe znaki XML, takie jak "&" i "<", muszą być kodowane jako jednostki ("&amp;" i "&lt;" itd.).

 Znak "i" w ciągu tekstowym określa skrót klawiaturowy dla polecenia.

## <a name="syntax"></a>Składnia

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|język|Opcjonalny. Language = ".".|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|ButtonText|To pole i pięć następujących pól tekstowych w definicji polecenia umożliwiają określenie tekstu wyświetlanego w różnych menu. Domyślnie pole `ButtonText` pojawia się w obszarze Kontrolery menu. Pole `ButtonText` również jest domyślnym ustawieniem, jeśli pozostałe pola tekstowe są puste. Pole `ButtonText` nie może być puste, nawet jeśli określono inne pola tekstowe.|
|ToolTipText|Pole `ToolTipText` określa tekst, który pojawia się w etykietce narzędzia dla elementu menu.<br /><br /> Jeśli pole `ToolTipText` jest puste, zostanie użyte pole `ButtonText`.|
|MenuText|Pole `MenuText` określa tekst, który jest wyświetlany dla polecenia, jeśli znajduje się w menu głównym, na pasku narzędzi w menu skrótów lub w podmenu. Jeśli pole `MenuText` jest puste, zintegrowane środowisko programistyczne (IDE) używa pola `ButtonText`. Pola `MenuText` można także użyć do lokalizacji.<br /><br /> W przypadku menu skrótów pole `MenuText` jest nazwą wyświetlaną na pasku narzędzi menu skrótów, co umożliwia dostosowywanie menu skrótów w środowisku IDE. W związku z tym należy określić, jak nazywa się menu skrótów; na przykład użyj "menu skrótów pakietu widżetu" zamiast "skrót".<br /><br /> Jeśli pole `MenuText` nie jest określone, używane jest pole `ButtonText`.|
|CommandName|Pole `CommandName` określa tekst, który pojawia się w kategorii klawiatura na karcie **polecenia** w oknie dialogowym **Dostosowywanie** (dostępne po kliknięciu pozycji **Dostosuj** w menu **Narzędzia** ).|
|CanonicalName|Pole `CanonicalName` w języku angielskim określa nazwę polecenia w tekocie w języku angielskim, którą można wprowadzić w oknie **polecenia** , aby wykonać element menu. IDE przykreśla wszystkie znaki, które nie są literami, cyframi, podkreśleniami lub osadzonymi kropkami. Ten tekst jest następnie łączony do pola `ButtonText`, aby zdefiniować polecenie. Na przykład **Nowy projekt** w menu **plik** jest poleceniem File. NewProject.<br /><br /> Jeśli pole `CanonicalName` w języku angielskim nie jest określone, IDE używa pola `ButtonText` i obejmuje wszystkie z wyjątkiem litery, cyfry, podkreślenia i kropki osadzone. Na przykład tekst przycisku "& Definiuj polecenia..." zostanie DefineCommands, gdzie znak handlowego "i", spacja i wielokropek są usuwane.<br /><br /> Jeśli flaga `TextChanges` jest określona i tekst polecenia zostanie zmieniony, odpowiednie polecenie rozpoznawane przez okno **polecenia** nie ulega zmianie; pozostaje to kanoniczna postać oryginalnych pól `ButtonText` lub `CanonicalName` w języku angielskim.|
|LocCanonicalName|Pole `LocCanonicalName` działa identycznie z polem `CanonicalName` w języku angielskim, ale umożliwia określenie zlokalizowanego tekstu polecenia. Można określić zarówno pola kanoniczne. Ze względu na to, że IDE analizuje tylko tekst wprowadzony w oknie **polecenia** i kojarzy je z poleceniem, zarówno tekst w języku angielskim, jak i innym niż angielski można skojarzyć z tym samym poleceniem.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Button, element](../extensibility/button-element.md)|Definiuje element, z którym użytkownik może korzystać.|
|[Menu, element](../extensibility/menu-element.md)|Definiuje pojedynczy element menu.|
|[Combo, element](../extensibility/combo-element.md)|Definiuje polecenia, które pojawiają się w polu kombi.|

## <a name="see-also"></a>Zobacz także
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)