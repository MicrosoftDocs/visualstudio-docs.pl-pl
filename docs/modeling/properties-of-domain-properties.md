---
title: Właściwości właściwości domeny
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 4359c71e054b8284e16eaed88b0ee140f7954494
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869456"
---
# <a name="properties-of-domain-properties"></a>Właściwości właściwości domeny
A *właściwość domeny* jest funkcją elementu modelu, który może zawierać wartości. Na przykład `Person` klasa domeny może mieć właściwości `Name` i `BirthDate`. W definicji DSL właściwości domeny są wyświetlane w polu Domena klas na diagramie, a w ramach klasy domeny w Eksplorator DSL. Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
>  Wyraz "property" ma dwa zastosowania. A *właściwość domeny* to funkcja, która definiuje się na klasę domeny. Z kolei ma wiele elementów języka DSL *właściwości*, które są wymienione w **właściwości** okna w definicji DSL. Na przykład dla każdej właściwości domeny ma zestaw właściwości, które są opisane w tym temacie.

 W czasie wykonywania, gdy użytkownik tworzy wystąpienia klasy domeny, wartości właściwości domeny są widoczne w oknie dialogowym właściwości i mogą być wyświetlane na kształty.

 Większość właściwości domeny są implementowane jako właściwości aparatu CLR zwykłej. Jednak z programowania punktu widzenia właściwości domeny mają więcej funkcji niż właściwości zwykłego programu:

- Można zdefiniować reguły i zdarzenia, które monitorują stan właściwości. Aby uzyskać więcej informacji, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

- Transakcje zapobiec niespójne stanów. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Po wybraniu Właściwość Domain w diagramie lub w Eksploratorze DSL, zobaczysz następujące elementy w oknie dialogowym właściwości. Aby uzyskać więcej informacji na temat używania tych elementów, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Wartość domyślna|
|-|-|-|
|**Opis**|Opis, który jest używany do dokumentów interfejsu użytkownika (UI) wygenerowanego projektanta.|\<Brak >|
|**Nazwa wyświetlana**|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej właściwości domeny. Może zawierać spacje i znaki interpunkcyjne, na przykład "utwór Title".|\<Brak >|
|**Dostawca nazw elementów**|Ma to zastosowanie tylko wtedy, gdy zostały ustawione `Is Element Name` do `true`. Można napisać kod, który zawiera nazwę dla nowego elementu klasę domeny Zastępowanie domyślnego zachowania.<br /><br /> W pliku kodu w projekcie języka DSL, należy utworzyć klasę, która jest pochodną <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> Następnie w Eksplorator DSL, kliknij prawym przyciskiem myszy katalog główny język DSL i kliknij przycisk Dodaj typ zewnętrzny. Wprowadź nazwę klasy.<br /><br /> Ponownie wybierz tę właściwość domeny, a następnie wybierz nazwę klasy na liście rozwijanej.|\<Brak >|
|**Modyfikator dostępu metody pobierającej**|Poziom dostępu dla klasy domeny (`public` lub `internal`). Ta opcja kontroluje zakresu, w jaki program kod może uzyskiwać dostęp do właściwości.|`public`|
|**Słowo kluczowe pomocy**|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tej właściwości domeny.|\<Brak >|
|**Jest możliwa do przeglądania**|Jeśli `True`, właściwość domeny jest wyświetlane użytkownikowi w oknie dialogowym właściwości, gdy modeli tego języka DSL są otwarte.<br /><br /> Jeśli `False`, właściwość domeny jest ukryty w interfejsie użytkownika.<br /><br /> Jeśli chcesz właściwość domeny widoczny, ale tylko do odczytu, ustaw **jest interfejs użytkownika tylko do odczytu**.|`True`|
|**Jest nazwą elementu**|Jeśli `True`, ta właściwość domeny, które będą wyświetlane jako nazwa elementu modelu w Eksplorator DSL.<br /><br /> Nowe elementy modelu otrzyma wartość domyślną unikatowy dla tej właściwości. Jeśli chcesz kontrolować, jak te wartości są generowane, ustaw **dostawca nazw elementów**.|`False`|
|**Interfejs użytkownika tylko do odczytu**|Jeśli `True`, nie można zmienić wartości właściwości domeny przy użyciu interfejsu użytkownika. Nadal można ustawić w programach i będą widoczne w oknie dialogowym właściwości.<br /><br /> Jeśli chcesz ukryć właściwość domeny użytkownika, ustaw **jest możliwa do przeglądania**. Jeśli chcesz kontrolować dostęp przez programy **modyfikator dostępu metody ustawiającej**.|`False`|
|**rodzaj**|Rodzaj właściwości domeny (`Normal`, `Calculated`, lub `CustomStorage`). Aby uzyskać więcej informacji, zobacz [obliczeniowe i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Nazwa**|Nazwa tej właściwości domeny. Jego musi być prawidłowym identyfikatorem, na przykład **SongTitle**.|\<Brak >|
|**Uwagi**|Uwagi informacyjne, które są skojarzone z tą właściwością domeny.|\<Brak >|
|**Modyfikator dostępu metody ustawiającej**|Modyfikator dostępu dla metody ustawiającej. Ta opcja kontroluje zakresu, w jaki program code można ustawić właściwości.|`public`|
|**Typ**|Typ właściwości. Aby dodać do listy dostępnych typów, kliknij prawym przyciskiem myszy katalog główny języka DSL w Eksplorator DSL, a następnie kliknij przycisk **Dodaj typ zewnętrzny**.|`String`|

## <a name="see-also"></a>Zobacz też

- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)