---
title: Właściwości diagramów
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: cf3405d74a1545bb86b1297b766faf46e68223a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942051"
---
# <a name="properties-of-diagrams"></a>Właściwości diagramów
Można ustawić właściwości, które określają, jak diagramy będzie wyświetlana w wygenerowanym projektancie. Na przykład można określić domyślny kolor tekstu na diagramie.

 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Poniższa tabela zawiera listę właściwości diagramów.

|Właściwość|Opis|Domyślny|
|-|-|-|
|Kolor wypełnienia|Kolor wypełnienia dla diagramu.|Biały|
|Kolor tekstu|Kolor tekstu, która jest wyświetlana na diagramie.|Czarny|
|Modyfikator dostępu|Modyfikator dostępu dla klasy (wewnętrznego lub publicznego).|Public|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy wygenerowanego kodu.|\<Brak >|
|Generuje Double pochodne|Jeśli `True`, zostaną wygenerowane klasy podstawowej i klasy częściowej (obsługuje dostosowywania przy użyciu zastąpień). Aby uzyskać więcej informacji, zobacz [zastąpienia i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Ma konstruktora niestandardowego|Jeśli `True`, konstruktora niestandardowego, które będą dostępne w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastąpienia i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|
|Modyfikator dziedziczenia|Opisuje typ dziedziczenia klasy kodu źródłowego, która jest generowany na podstawie diagramu (`none`, `abstract`, lub `sealed`).|Brak|
|Podstawowy Diagram|Klasa bazowa ten diagram.|(Brak)|
|Nazwa|Nazwa tego diagramu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym diagramie.|Bieżąca przestrzeń nazw|
|Reprezentowana klasa|Klasa domeny katalogu głównego ten diagram przedstawia.|Bieżąca klasa głównego, jeśli ma to zastosowanie|
|Uwagi|Uwagi informacyjne, które są skojarzone z tym elementem.|\<Brak >|
|Kolor wypełnienia ujawnia jako właściwość|Jeśli `True`, użytkownik może ustawić kolor wypełnienia diagram wygenerowanego projektanta. Aby ustawić tę właściwość, kliknij prawym przyciskiem myszy kształt diagramu, a następnie kliknij przycisk **Dodaj udostępniane**.|False|
|Opisuje kolor tekstu jako właściwość|Jeśli `True`, użytkownik może ustawić kolor tekstu diagramu w wygenerowanym projektancie. Aby ustawić tę właściwość, kliknij prawym przyciskiem myszy kształt diagramu, a następnie kliknij przycisk **Dodaj udostępniane**.|False|
|Opis|Opis, który jest używany do dokumentu wygenerowanego projektanta.|\<Brak >|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tego diagramu.|\<Brak >|
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla okna ten diagram.|\<Brak >|

## <a name="see-also"></a>Zobacz także

[Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
