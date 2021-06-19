---
title: Właściwości diagramów
description: Dowiedz się więcej na temat diagramów i sposobu określania właściwości, które określają sposób, w jaki diagramy będą wyświetlane w wygenerowanym projektancie.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8a060c79866d1746135f8a29aef15ca96dd51f63
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390675"
---
# <a name="properties-of-diagrams"></a>Właściwości diagramów
Możesz ustawić właściwości, które określają sposób, w jaki diagramy będą wyświetlane w wygenerowanym projektancie. Na przykład można określić domyślny kolor tekstu na diagramie.

 Aby uzyskać więcej informacji, [zobacz How to define a domain-specific language](../modeling/how-to-define-a-domain-specific-language.md)(Jak zdefiniować język specyficzny dla domeny). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i rozszerzanie języka [specyficznego dla domeny.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 W poniższej tabeli wymieniono właściwości diagramów.

|Właściwość|Opis|Domyślne|
|-|-|-|
|Kolor wypełnienia|Kolor wypełnienia diagramu.|Biały|
|Kolor tekstu|Kolor tekstu wyświetlanego na diagramie.|Czarnoskórzy|
|Modyfikator dostępu|Modyfikator dostępu klasy (publiczny lub wewnętrzny).|Publiczne|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do wygenerowanej klasy kodu.|\<none>|
|Generuje podwójne pochodne|Jeśli zostanie wygenerowana zarówno klasa bazowa, jak i klasa częściowa (w celu obsługi `True` dostosowywania za pomocą zastąpień). Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Ma niestandardowy konstruktor|Jeśli `True` , niestandardowy konstruktor zostanie podany w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [Override and extend the generated classes](../modeling/overriding-and-extending-the-generated-classes.md)..|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego generowanego na podstawie diagramu ( `none` `abstract` , lub `sealed` ).|Brak|
|Diagram podstawowy|Klasa bazowa tego diagramu.|(brak)|
|Nazwa|Nazwa tego diagramu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw powiązana z tym diagramem.|Bieżąca przestrzeń nazw|
|Reprezentowana klasa|Klasa domeny głównej, która reprezentuje ten diagram.|Bieżąca klasa główna, jeśli ma zastosowanie|
|Uwagi|Notatki nieformalne skojarzone z tym elementem.|\<none>|
|Uwidacznia właściwość Fill Color As|Jeśli `True` ma wartość , użytkownik może ustawić kolor wypełnienia diagramu wygenerowanego projektanta. Aby ustawić tę właściwość, kliknij prawym przyciskiem myszy kształt diagramu i kliknij polecenie **Dodaj ujawnione**.|Fałsz|
|Uwidacznia kolor tekstu jako właściwość|Jeśli ma wartość , użytkownik może `True` ustawić kolor tekstu diagramu w wygenerowanym projektancie. Aby ustawić tę właściwość, kliknij prawym przyciskiem myszy kształt diagramu i kliknij polecenie **Dodaj ujawnione**.|Fałsz|
|Opis|Opis używany do dokumentować wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego diagramu.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe używane do indeksowania pomocy F1 dla tego diagramu.|\<none>|

## <a name="see-also"></a>Zobacz też

[Słownik narzędzi językowych specyficznych dla domeny](/previous-versions/bb126564(v=vs.100))