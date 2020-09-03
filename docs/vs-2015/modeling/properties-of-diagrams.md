---
title: Właściwości diagramów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31fb06512457f919b67d41c3fb4096e4c3477426
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652028"
---
# <a name="properties-of-diagrams"></a>Właściwości diagramów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można ustawić właściwości określające sposób wyświetlania diagramów w wygenerowanym projektancie. Na przykład można określić domyślny kolor tekstu na diagramie.

 Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Poniższa tabela zawiera listę właściwości diagramów.

|Właściwość|Opis|Domyślne|
|--------------|-----------------|-------------|
|Kolor wypełnienia|Kolor wypełnienia dla diagramu.|Biały|
|Kolor tekstu|Kolor tekstu, który jest wyświetlany na diagramie.|Czarnoskórzy|
|Modyfikator dostępu|Modyfikator dostępu klasy (Public lub internal).|Publiczne|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do wygenerowanej klasy kodu.|\<none>|
|Generuje podwójny pochodny|Jeśli `True` , zostanie wygenerowany zarówno klasę bazową, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|Fałsz|
|Ma Konstruktor niestandardowy|Jeśli `True` w kodzie źródłowym zostanie podany Konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md)..|Fałsz|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana na podstawie diagramu ( `none` `abstract` lub `sealed` ).|Brak|
|Diagram podstawowy|Klasa bazowa tego diagramu.|(brak)|
|Nazwa|Nazwa tego diagramu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest powiązana z tym diagramem.|Bieżąca przestrzeń nazw|
|Reprezentowane klasy|Klasa domeny głównej, którą reprezentuje ten diagram.|Bieżąca Klasa główna, jeśli ma zastosowanie|
|Uwagi|Nieformalne uwagi, które są skojarzone z tym elementem.|\<none>|
|Uwidacznia kolor wypełnienia jako właściwość|Jeśli `True` użytkownik może ustawić kolor wypełnienia diagramu wygenerowanego projektanta. Aby ustawić tę opcję, kliknij prawym przyciskiem myszy kształt diagramu i kliknij polecenie **Dodaj eXplosed**.|Fałsz|
|Uwidacznia kolor tekstu jako właściwość|Jeśli `True` użytkownik może ustawić kolor tekstu diagramu w wygenerowanym projektancie. Aby ustawić tę opcję, kliknij prawym przyciskiem myszy kształt diagramu i kliknij polecenie **Dodaj eXplosed**.|Fałsz|
|Opis|Opis używany do dokumentowania wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego diagramu.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego diagramu.|\<none>|

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
