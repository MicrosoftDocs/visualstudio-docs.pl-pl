---
title: Modelowanie &apos; architektury aplikacji
description: Dowiedz się, jak można tworzyć modele w Visual Studio w ramach opisu ogólnej struktury i zachowania systemu oprogramowania lub aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa2be8f4da963c21d9f7f68939421dd7d2d72d0b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390115"
---
# <a name="model-your-app39s-architecture"></a>Modelowanie aplikacji&#39;architektury
Aby mieć pewność, że system oprogramowania lub aplikacja spełnia potrzeby użytkowników, możesz tworzyć modele w programie Visual Studio jako część opisu ogólnej struktury i zachowania systemu oprogramowania lub aplikacji. Korzystając z modeli, można również opisać wzorce używane w całym projekcie. Te modele pomagają zrozumieć istniejącą architekturę, omówić zmiany i wyraźnie przekazać swoje intencje.

 Aby sprawdzić, które wersje Visual Studio tej funkcji, zobacz Obsługa wersji dla architektury [i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

 Celem modelu jest zmniejszenie niejednoznaczności, które występują w opisach w języku naturalnym, oraz pomoc Ci i Twoim współpracownikom w wizualizacji projektu i omawiania alternatywnych projektów. Model powinien być używany razem z innymi dokumentami lub dyskusjami. Sam model nie reprezentuje pełnej specyfikacji architektury.

> [!NOTE]
> W tym temacie "system" oznacza oprogramowanie, które opracowujesz. Może to być duża kolekcja wielu składników oprogramowania i sprzętu, pojedyncza aplikacja lub część aplikacji.

 Architekturę systemu można podzielić na dwa obszary:

- [Projekt wysokiego poziomu](#Structure). W tym artykule opisano główne składniki oraz sposób, w jaki współdziałają ze sobą w celu spełnienia poszczególnych wymagań. Jeśli system jest duży, każdy składnik może mieć własny projekt wysokiego poziomu, który pokazuje, jak składa się z mniejszych składników.

- [Wzorce](#Patterns) projektowe i konwencje używane w projektach składników. Wzorzec opisuje konkretne podejście do osiągnięcia celu programistycznego. Korzystając z tych samych wzorców w całym projekcie, twój zespół może zmniejszyć koszt dokonywania zmian i opracowywania nowego oprogramowania.

## <a name="high-level-design"></a><a name="Structure"></a> Projekt wysokiego poziomu
 Projekt wysokiego poziomu opisuje główne składniki systemu i sposób, w jaki współdziałają ze sobą w celu osiągnięcia celów projektu. Działania na poniższej liście są związane z opracowywaniem projektu wysokiego poziomu, chociaż niekoniecznie w określonej kolejności.

 Jeśli aktualizujesz istniejący kod, możesz zacząć od opisania głównych składników. Upewnij się, że rozumiesz wszelkie zmiany wymagań użytkownika, a następnie dodaj lub zmodyfikuj interakcje między składnikami. Jeśli opracowujesz nowy system, zacznij od zrozumienia głównych funkcji potrzeb użytkowników. Następnie możesz eksplorować sekwencje interakcji dla głównych przypadków użycia, a następnie konsolidować sekwencje w projekcie składnika.

 W każdym przypadku pomocne jest równoległe opracowywanie różnych działań oraz opracowywanie kodu i testów na wczesnym etapie. Unikaj próby ukończenia jednego z tych aspektów przed rozpoczęciem innego. Zwykle wymagania i zrozumienie najlepszego sposobu projektowania systemu zmieni się podczas pisania i testowania kodu. W związku z tym należy zacząć od zrozumienia i kodowania głównych funkcji wymagań i projektu. Wypełnij szczegóły w kolejnych iteracjach projektu.

- [Opis wymagań](#Requirements). Punktem początkowym każdego projektu jest jasne zrozumienie potrzeb użytkowników.

- [Wzorce architektury](#BigDecisions). Dokonane wybory dotyczące podstawowych technologii i elementów architektury systemu.

- Model danych składników i interfejsów. Można rysować diagramy klas, aby opisać informacje przekazywane między składnikami i przechowywane wewnątrz składników.

## <a name="understanding-the-requirements"></a><a name="Requirements"></a> Opis wymagań
 Ogólny projekt kompletnej aplikacji jest najbardziej efektywnie opracowywany wraz z modelem wymagań lub innym opisem potrzeb użytkowników. Aby uzyskać więcej informacji na temat modeli wymagań, zobacz [Wymagania użytkownika modelu](../modeling/model-user-requirements.md).

 Jeśli system, który opracowujesz, jest składnikiem większego systemu, część lub wszystkie wymagania mogą być ujmowane w interfejsy programowe.

 Model wymagań zawiera następujące podstawowe informacje:

- Dostarczone interfejsy. Podany interfejs zawiera listę usług lub operacji, które system lub składnik musi udostępnić swoim użytkownikom, niezależnie od tego, czy są użytkownikami, czy innymi składnikami oprogramowania.

- Wymagane interfejsy. Wymagany interfejs zawiera listę usług lub operacji, z których może korzystać system lub składnik. W niektórych przypadkach będzie można zaprojektować wszystkie te usługi jako część własnego systemu. W innych przypadkach, szczególnie w przypadku projektowania składnika, który może być połączony z innymi składnikami w wielu konfiguracjach, wymagany interfejs zostanie ustawiony przez zewnętrzne zagadnienia.

- Jakość wymagań dotyczących usługi. Wydajność, zabezpieczenia, niezawodność oraz inne cele i ograniczenia, które musi spełniać system.

  Model wymagań jest napisany z punktu widzenia użytkowników systemu, niezależnie od tego, czy są to ludzie, czy inne składniki oprogramowania. Nie wiedzą nic o wewnętrznych działaniach systemu. Z kolei twoim celem w modelu architektonicznym jest opisanie wewnętrznych prac i pokazanie, jak spełniają one potrzeby użytkowników.

  Utrzymywanie oddzielnych wymagań i modeli architektonicznych jest przydatne, ponieważ ułatwia omawianie wymagań z użytkownikami. Pomaga również refaktoryzować projekt i uwzględniać alternatywne architektury przy zachowaniu niezmienionych wymagań.

  Ilość szczegółów, które należy umieścić w wymaganiach lub modelu architektonicznym, zależy od skali projektu oraz rozmiaru i rozkładu zespołu. Mały zespół w krótkim projekcie może nie tylko naszkicować diagram klas koncepcji biznesowych i pewne wzorce projektowe; duży projekt rozproszony w więcej niż jednym regionie wymagałby znacznie większej liczby szczegółów.

## <a name="architectural-patterns"></a><a name="BigDecisions"></a> Wzorce architektoniczne
 Na wczesnym etapie opracowywania należy wybrać główne technologie i elementy, od których zależy projekt. Do obszarów, w których należy wybrać te opcje, należą:

- Podstawowe opcje technologiczne, takie jak wybór między bazą danych a systemem plików, wybór między aplikacją sieciową a klientem internetowym i tak dalej.

- Struktury do wyboru, takie jak wybór między Windows Workflow Foundation lub ADO.NET Entity Framework.

- Opcje metody integracji, na przykład między magistralą usług przedsiębiorstwa lub kanałem typu punkt-punkt.

  Te opcje są często określane przez jakość wymagań dotyczących usług, takich jak skalowanie i elastyczność, i mogą być dokonywane, zanim zostaną znane szczegółowe wymagania. W dużym systemie konfiguracja sprzętu i oprogramowania jest silnie powiązana.

  Wybrane opcje mają wpływ na sposób używania i interpretowania modelu architektonicznego. Na przykład w systemie, który używa bazy danych, skojarzenia w diagramie klas mogą reprezentować relacje lub klucze obce w bazie danych, natomiast w systemie opartym na plikach XML skojarzenia mogą wskazywać odwołania krzyżowe, które używają XPath. W systemie rozproszonym komunikaty na diagramie sekwencji mogą reprezentować komunikaty w sieci; W aplikacji samodzielnej mogą reprezentować wywołania funkcji.

## <a name="design-patterns"></a><a name="Patterns"></a> Wzorce projektowe
 Wzorzec projektowy to konspekt sposobu projektowania określonego aspektu oprogramowania, szczególnie tego, który powtarza się w różnych częściach systemu. Przyjmując jednolite podejście w całym projekcie, można zmniejszyć koszty projektowania, zapewnić spójność w interfejsie użytkownika oraz zmniejszyć koszt zrozumienia i zmiany kodu.

 Niektóre ogólne wzorce projektowe, takie jak Obserwator, są dobrze znane i powszechnie stosowane. Ponadto istnieją wzorce, które mają zastosowanie tylko do projektu. Na przykład w systemie sprzedaży internetowej w kodzie będzie wykonywanych kilka operacji, w których są dokonywane zmiany w zamówieniu klienta. Aby upewnić się, że stan zamówienia jest dokładnie wyświetlany na każdym etapie, wszystkie te operacje muszą być wykonywane zgodnie z konkretnym protokołem w celu zaktualizowania bazy danych.

 Częścią pracy architektury oprogramowania jest określenie wzorców, które należy stosować w całym projekcie. Jest to zwykle ciągłe zadanie, ponieważ nowe wzorce i ulepszenia istniejących wzorców będą odkrywane w trakcie realizacji projektu. Warto zorganizować plan rozwoju tak, aby na wczesnym etapie ćwiczyć każdy z głównych wzorców projektowych.

 Większość wzorców projektowych może być częściowo uosabowana w kodzie struktury. Część wzorca można ograniczyć do wymagania od dewelopera używania określonych klas lub składników, takich jak warstwa dostępu do bazy danych, która zapewnia, że baza danych jest prawidłowo obsłużona.

 Wzorzec projektowy jest opisany w dokumencie i zazwyczaj zawiera następujące części:

- Nazwa.

- Opis kontekstu, w którym ma zastosowanie. Jakie kryteria powinny sprawić, że deweloper rozważy zastosowanie tego wzorca?

- Krótkie wyjaśnienie problemu, który rozwiązuje.

- Model głównych części i ich relacji. Mogą to być klasy lub składniki i interfejsy ze skojarzeniami i zależnościami między nimi. Elementy zazwyczaj można ująć w dwie kategorie:

- Konwencje nazewnictwa.

- Opis sposobu rozwiązania problemu przez wzorzec.

- Opis odmian, które deweloperzy mogą być w stanie adoptować.

## <a name="see-also"></a>Zobacz też

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
