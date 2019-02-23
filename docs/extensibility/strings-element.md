---
title: Ciągi Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de2ed5d9c757d9082cd06c2aae5a8e51b0865714
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699408"
---
# <a name="strings-element"></a>Strings, element
Strings, element musi zawierać co najmniej jeden **ButtonText** elementu podrzędnego. Wszystkie inne elementy podrzędne są opcjonalne. Nieprawidłowy kod XML znaków takich jak "&" i "<" musi być kodowane jako jednostki ("&amp;"i"&lt;" i tak dalej).

 Handlowe "i" w ciągu tekstowym określa skrótu klawiaturowego dla polecenia.

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
|język|Opcjonalna. Language=".".|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|ButtonText|To pole i pięć następujących pól tekstowych w definicji polecenia pozwalają określić tekst, który pojawia się w różnych menu. Domyślnie `ButtonText` pole jest wyświetlane w menu kontrolerów. `ButtonText` Pole staje się również wartość domyślna Jeśli inne pola tekstowe są puste. `ButtonText` Pole nie może być pusta, nawet jeśli inne pola tekstowe są określone.|
|ToolTipText|`ToolTipText` Pole określa tekst wyświetlany w etykietce narzędzia dla elementu menu.<br /><br /> Jeśli `ToolTipText` pole jest puste, `ButtonText` pole jest używane.|
|MenuText|`MenuText` Pole określa tekst, który jest wyświetlany dla polecenia, jeśli znajduje się w menu głównym pasku narzędzi, w menu skrótów lub w podmenu. Jeśli `MenuText` pole jest puste, zintegrowanego środowiska programistycznego (IDE) korzysta `ButtonText` pola. `MenuText` Pola może również służyć do lokalizacji.<br /><br /> Menu skrótów `MenuText` pole jest nazwa, która jest wyświetlana na pasku menu skrótów, co umożliwia dostosowanie menu skrótów w środowisku IDE. Zatem określonego w co nazwy z menu skrótów. na przykład użyć "Widżet Menu skrótu pakietu" zamiast "Skrótu".<br /><br /> Jeśli `MenuText` pole nie zostanie określony, `ButtonText` pole jest używane.|
|commandName|`CommandName` Pole określa tekst, który pojawia się w kategorii klawiatury w **polecenia** karcie **Dostosuj** okno dialogowe (dostępna przez kliknięcie przycisku **Dostosuj**na **narzędzia** menu).|
|CanonicalName|Angielska `CanonicalName` pola określa nazwę polecenia w tekstu w języku angielskim, które mogą być wprowadzane w **polecenia** okna do wykonania elementu menu. Paski IDE się żadnych znaków, które nie są litery, cyfry, podkreślenia i okresów osadzonego. Ten tekst jest następnie łączone w celu `ButtonText` pola do definiowania polecenia. Na przykład **nowy projekt** na **pliku** menu staje się polecenie File.NewProject.<br /><br /> Jeśli angielska `CanonicalName` pole nie zostanie określony, IDE używa `ButtonText` pola i paski wszystkie z wyjątkiem litery, cyfry, podkreślenia i okresów osadzonych. Na przykład tekst przycisku "i zdefiniuj polecenia..." staje się DefineCommands, gdzie handlowe "i", miejsce i wielokropek są usuwane.<br /><br /> Jeśli `TextChanges` flaga zostanie określona, tekst polecenia nie zostanie zmieniony, odpowiednie polecenie, które są rozpoznawane przez **polecenia** okna nie zmienia; pozostanie forma kanoniczna oryginalny `ButtonText` lub wjęzykuangielskim`CanonicalName` pola.|
|LocCanonicalName|`LocCanonicalName` Pola działa identycznie do języka angielskiego `CanonicalName` pola umożliwia jednak tekst polecenia zlokalizowane określenie. Można określić obu pól kanonicznej. Ponieważ IDE analizuje tekst wprowadzony w **polecenia** okna i kojarzy z poleceniem, zarówno w języku angielskim, jak i w innych niż angielski tekst może być skojarzony z tym samym poleceniu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Button, element](../extensibility/button-element.md)|Definiuje element, który użytkownik może interakcyjnie przeprowadzić.|
|[Menu, element](../extensibility/menu-element.md)|Definiuje pojedynczy element menu.|
|[Combo, element](../extensibility/combo-element.md)|Określa polecenia, które są wyświetlane w polu kombi.|

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)