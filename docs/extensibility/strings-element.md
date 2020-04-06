---
title: Element strun | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699721"
---
# <a name="strings-element"></a>Strings, element
Strings element musi zawierać co najmniej **ButtonText** element podrzędny. Wszystkie inne elementy podrzędne są opcjonalne. Nieprawidłowe znaki XML, takie jak "&" i "<" muszą być kodowane jako jednostki ('&amp;' i '&lt;' itd.).

 Ciąg ampersand w ciągu tekstowym określa skrót klawiaturowy polecenia.

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
|language|Element opcjonalny. Language=".".|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Buttontext|To pole i pięć następujących pól tekstowych w definicji polecenia umożliwia określenie tekstu wyświetlanego w różnych menu. Domyślnie `ButtonText` pole jest wyświetlane w kontrolerach menu. Pole `ButtonText` staje się również wartością domyślną, jeśli inne pola tekstowe są puste. Pole `ButtonText` nie może być puste, nawet jeśli określono inne pola tekstowe.|
|Tooltiptext|Pole `ToolTipText` określa tekst wyświetlany w etykietce narzędzia elementu menu.<br /><br /> Jeśli `ToolTipText` pole jest puste, `ButtonText` pole jest używane.|
|MenuTekst|Pole `MenuText` określa tekst wyświetlany dla polecenia, jeśli znajduje się w menu głównym, pasku narzędzi, w menu skrótów lub w podmenu. Jeśli `MenuText` pole jest puste, zintegrowane środowisko programistyczne `ButtonText` (IDE) używa tego pola. Pole `MenuText` może być również używane do lokalizacji.<br /><br /> W przypadku menu `MenuText` skrótów pole jest nazwą wyświetlaną na pasku narzędzi Menu skrótów, która umożliwia dostosowywanie menu skrótów w idei. W związku z tym, być specyficzne w tym, co nazwa menu skrótów; na przykład użyj "Menu skrótów pakietu widżetu" zamiast "Skrót".<br /><br /> Jeśli `MenuText` pole nie jest `ButtonText` określone, pole jest używane.|
|Commandname|Pole `CommandName` określa tekst wyświetlany w kategorii klawiatury na karcie **Polecenia** w oknie dialogowym **Dostosowywanie** (dostępne po **kliknięciu** menu Dostosuj w menu **Narzędzia).**|
|Nazwa kanoniczna|Pole `CanonicalName` w języku angielskim określa nazwę polecenia w tekście w języku angielskim, które można wprowadzić w oknie **Polecenia** w celu wykonania elementu menu. IDE usuwa wszystkie znaki, które nie są literami, cyframi, podkreśleniami lub kropkami osadzonymi. Ten tekst jest następnie łączony z polem w `ButtonText` celu zdefiniowania polecenia. Na przykład **nowy projekt** w menu **Plik** staje się poleceniem File.NewProject.<br /><br /> Jeśli pole `CanonicalName` angielskie nie jest określone, `ButtonText` IDE używa tego pola i usuwa wszystkie z wyjątkiem liter, cyfr, podkreśleń i okresów osadzonych. Na przykład tekst przycisku "&zdefiniuj polecenia..." defineCommands, gdzie ampersand, przestrzeń i wielokropek są usuwane.<br /><br /> Jeśli `TextChanges` flaga jest określona, a tekst polecenia zostanie zmieniony, odpowiednie polecenie rozpoznawane przez okno **Polecenie** nie ulega zmianie; pozostaje kanoniczną formą pól `ButtonText` oryginalnych `CanonicalName` lub angielskich.|
|Nazwa LocCanonicalName|Pole `LocCanonicalName` zachowuje się identycznie `CanonicalName` jak pole angielskie, ale umożliwia określanie zlokalizowanych tekstów poleceń. Można określić oba pola kanoniczne. Ponieważ IDE tylko analizuje tekst wprowadzony w oknie **polecenia** i kojarzy go z poleceniem, tekst w języku angielskim i nieanglojęzycznym może być skojarzony z tym samym poleceniem.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Button, element](../extensibility/button-element.md)|Definiuje element, z który użytkownik może wchodzić w interakcje.|
|[Menu, element](../extensibility/menu-element.md)|Definiuje pojedynczy element menu.|
|[Combo, element](../extensibility/combo-element.md)|Definiuje polecenia wyświetlane w polu kombi.|

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
