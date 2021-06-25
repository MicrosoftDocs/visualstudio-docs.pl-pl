---
title: Strings, element | Microsoft Docs
description: Element Strings zawiera element podrzędny ButtonText i inne opcjonalne elementy podrzędne. Znak ampersand w ciągu tekstowym określa skrót klawiaturowy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27a649c7d3a8bb808153c280921d2304de59c379
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899410"
---
# <a name="strings-element"></a>Strings, element
Element Strings musi zawierać co najmniej element **podrzędny ButtonText.** Wszystkie inne elementy podrzędne są opcjonalne. Nieprawidłowe znaki XML, takie jak "&" i "<", muszą być zakodowane jako jednostki (' &amp; ' i ' ' &lt; itd.).

 Znak ampersand w ciągu tekstowym określa skrót klawiaturowy dla polecenia.

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
|language|Opcjonalny. Language=".".|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Buttontext|To pole i pięć poniższych pól tekstowych w definicji polecenia umożliwia określenie tekstu, który będzie wyświetlany w różnych menu. Domyślnie pole jest `ButtonText` wyświetlane w kontrolerach menu. Pole `ButtonText` staje się również wartością domyślną, jeśli inne pola tekstowe są puste. Pole `ButtonText` nie może być puste, nawet jeśli określono inne pola tekstowe.|
|Tooltiptext|Pole określa tekst wyświetlany w etykietce narzędzia `ToolTipText` elementu menu.<br /><br /> Jeśli pole `ToolTipText` jest puste, `ButtonText` zostanie użyte.|
|Tekst Menu|Pole określa tekst, który jest wyświetlany dla polecenia, jeśli znajduje się w menu głównym, na pasku `MenuText` narzędzi, w menu skrótów lub w podmenu. Jeśli pole `MenuText` jest puste, zintegrowane środowisko projektowe (IDE) używa `ButtonText` tego pola. Pola `MenuText` można również użyć do lokalizacji.<br /><br /> W przypadku menu skrótów pole jest nazwą wyświetlaną na pasku narzędzi Menu skrótów, co umożliwia dostosowywanie `MenuText` menu skrótów w ide. W związku z tym należy konkretną nazwę w menu skrótów; na przykład użyj opcji "Widget Package Shortcut Menu" zamiast "Shortcut".<br /><br /> Jeśli `MenuText` pole nie zostanie określone, `ButtonText` zostanie użyte.|
|Commandname|Pole określa tekst wyświetlany w kategorii klawiatury na karcie Polecenia w oknie dialogowym Dostosowywanie (dostępne po kliknięciu pozycji Dostosuj w `CommandName` menu Narzędzia).    |
|CanonicalName|Pole angielskie określa nazwę polecenia w tekście w języku angielskim, który można wprowadzić w oknie `CanonicalName` Polecenia, aby wykonać element menu.  Ide rozsyła wszystkie znaki, które nie są literami, cyframi, podkreśleniami ani osadzonymi kropkami. Ten tekst jest następnie łączyny z `ButtonText` polem w celu zdefiniowania polecenia. Na przykład **nowy projekt** w menu **Plik** staje się poleceniem File.NewProject.<br /><br /> Jeśli pole w języku angielskim nie jest określone, ide używa pola i rozsyła wszystkie litery, cyfry, podkreślenia i `CanonicalName` `ButtonText` kropki osadzone. Na przykład tekst przycisku "&polecenia..." staje się DefineCommands, gdzie ampersand, spacja i wielokropek są usuwane.<br /><br /> Jeśli flaga jest określona i tekst polecenia zostanie zmieniony, odpowiednie polecenie rozpoznane przez okno polecenia nie zmienia się; pozostaje formą kanoniczną oryginalnych lub `TextChanges`  `ButtonText` angielskich `CanonicalName` pól.|
|LocCanonicalName|Pole działa identycznie jak pole w `LocCanonicalName` języku angielskim, ale umożliwia określony zlokalizowany tekst `CanonicalName` polecenia. Można określić oba pola kanoniczne. Ponieważ idee po prostu analizuje  tekst wprowadzony w oknie Polecenia i kojarzy go z poleceniem, tekst w języku angielskim i innym niż angielski może być skojarzony z tym samym poleceniem.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Button, element](../extensibility/button-element.md)|Definiuje element, z który użytkownik może wchodzić w interakcje.|
|[Menu, element](../extensibility/menu-element.md)|Definiuje pojedynczy element menu.|
|[Combo, element](../extensibility/combo-element.md)|Definiuje polecenia, które są wyświetlane w polu kombi.|

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
