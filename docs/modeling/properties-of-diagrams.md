---
title: Właściwości diagramów
description: Dowiedz się więcej o diagramach i sposobach ustawiania właściwości, które określają sposób wyświetlania diagramów w wygenerowanym projektancie.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 943b634114c28f6f914926c74861a902c663523e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956168"
---
# <a name="properties-of-diagrams"></a>Właściwości diagramów
Można ustawić właściwości określające sposób wyświetlania diagramów w wygenerowanym projektancie. Na przykład można określić domyślny kolor tekstu na diagramie.

 Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat sposobu korzystania z tych właściwości, zobacz [Dostosowywanie i poszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Poniższa tabela zawiera listę właściwości diagramów.

|Właściwość|Opis|Domyślne|
|-|-|-|
|Kolor wypełnienia|Kolor wypełnienia dla diagramu.|Biały|
|Kolor tekstu|Kolor tekstu, który jest wyświetlany na diagramie.|Czarnoskórzy|
|Modyfikator dostępu|Modyfikator dostępu klasy (Public lub internal).|Publiczne|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do wygenerowanej klasy kodu.|\<none>|
|Generuje podwójny pochodny|Jeśli `True` , zostanie wygenerowany zarówno klasę bazową, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [Przesłoń i rozwiń wygenerowane klasy](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Ma Konstruktor niestandardowy|Jeśli `True` w kodzie źródłowym zostanie podany Konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [Przesłoń i rozwiń wygenerowane klasy](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana na podstawie diagramu ( `none` , `abstract` lub `sealed` ).|Brak|
|Diagram podstawowy|Klasa bazowa tego diagramu.|(brak)|
|Nazwa|Nazwa tego diagramu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest powiązana z tym diagramem.|Bieżąca przestrzeń nazw|
|Reprezentowane klasy|Klasa domeny głównej, którą reprezentuje ten diagram.|Bieżąca Klasa główna, jeśli ma zastosowanie|
|Uwagi|Nieformalne uwagi, które są skojarzone z tym elementem.|\<none>|
|Uwidacznia kolor wypełnienia jako właściwość|Jeśli `True` użytkownik może ustawić kolor wypełnienia diagramu wygenerowanego projektanta. Aby ustawić tę właściwość, kliknij prawym przyciskiem myszy kształt diagramu, a następnie kliknij pozycję **Dodaj uwidocznione**.|Fałsz|
|Uwidacznia kolor tekstu jako właściwość|Jeśli `True` użytkownik może ustawić kolor tekstu diagramu w wygenerowanym projektancie. Aby ustawić tę właściwość, kliknij prawym przyciskiem myszy kształt diagramu, a następnie kliknij pozycję **Dodaj uwidocznione**.|Fałsz|
|Opis|Opis używany do dokumentowania wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego diagramu.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego diagramu.|\<none>|

## <a name="see-also"></a>Zobacz też

[Słownik narzędzi języka specyficznego dla domeny](/previous-versions/bb126564(v=vs.100))