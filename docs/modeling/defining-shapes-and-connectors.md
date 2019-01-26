---
title: Definiowanie kształtów i łączników
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: edf82cde2674b91954737973ddfa37e738ff8ec1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016931"
---
# <a name="defining-shapes-and-connectors"></a>Definiowanie kształtów i łączników
Istnieje kilka typów podstawowych kształtów, które mogą być używane do wyświetlania informacji na diagramie w języku specyficznym dla domeny (DSL).

##  <a name="shapeTypes"></a> Podstawowe typy kształtów i łączników
 DSL diagram zawiera zbiór *kształty* powiązane liniami lub *łączników*.  Zwykle, ale nie zawsze:

- Kształty są widoczne reprezentacja elementów modelu.

- Łączniki reprezentują relacje odniesienia.

- Diagram przedstawia wystąpienie katalogu głównego modelu.

- Osadzanie relacje między elementami modelu są wyświetlane przez relację zawierania. Na przykład elementów reprezentujących porty składnika są osadzone w składniku.

  Te wzorce nie są wymuszane, ale mocno są obsługiwane. Podczas projektowania DSL ponosi należy pamiętać, że projekt relacji osadzania powinien być wpływ, jaki chcesz przedstawić modelu na ekranie. Z drugiej strony relacje odniesienia powinien odzwierciedlać pojęcia domeny biznesowej.

  Dostępne są następujące typy kształtów:

|Typ kształtu|Opis|
|-|-|
|Kształt geometryczny|Kształt prostokątne lub eliptycznego ogólnego przeznaczenia. Możesz wyświetlić tekst i ikona dekoratory w określonym położeniu względem granic kształtu.<br /><br /> Aby zagnieździć kształty wewnątrz kształtów geometrycznych, zobacz [zagnieżdżanie kształtów](../modeling/nesting-shapes.md).|
|Kształt przedziału|Prostokąt zawierający nagłówek i przedziały, takich jak klasy UML. Każdego przedziału może zawierać listę wierszy tekstu.<br /><br /> Wiersze reprezentują zazwyczaj elementy osadzone w elemencie reprezentowany przez kształt. Na przykład utworzyć DSL za pomocą szablonu rozwiązania diagramów klas.|
|Kształt obrazu|Kształt wyświetlający obraz.|
|Kształt portu|Niewielki prostokąt przeznaczone do dołączenia do konturu innego kształtu. Zazwyczaj używane w modelach składnika.<br /><br /> Element modelu reprezentowanego przez port jest zwykle osadzona w element reprezentowany przez kształtu nadrzędnego. Na przykład utworzyć DSL za pomocą szablonu rozwiązania składniki.<br /><br /> Domyślnie kształt portu można przesunąć wzdłuż boków jego obiektu nadrzędnego. Można zdefiniować zasadę granice, aby ograniczyć go do określonej pozycji.<br /><br /> Tworząc kształt portu bardzo małe i przejrzystości, umożliwia on stanowią punkt połączenia stałej powierzchni z boku jego kształtu nadrzędnego.|
|Torów|Tory podzielić diagramu na poziomą lub pionową segmentów. Tor zawsze pozostaje poniżej innych kształtów na diagramie.<br /><br /> Zazwyczaj elementy modelu toru są elementem nadrzędnym w katalogu głównym modelu i inne elementy są elementem nadrzędnym na nich. Na przykład utworzyć DSL za pomocą szablonu rozwiązania przepływu zadań.|
|Łączniki|Linii między kształtami zazwyczaj reprezentują relacje odniesienia. Można ustawić opcje, aby bezpośrednio lub prostoliniowego łącznika i mają różne typy grot strzałki.|

##  <a name="shapeInheritance"></a> Kształt dziedziczenia
 Kształt może dziedziczyć z innego kształtu. Jednak kształty muszą być tego samego rodzaju. Na przykład kształt geometryczny może dziedziczyć kształt geometryczny. Kształty dziedziczone mają przedziały i dekoratory ich kształtu podstawowego. Łączniki mogą dziedziczyć łączników.