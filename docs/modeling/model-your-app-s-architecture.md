---
title: Model aplikacji&#39;architektury s
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 56b3d76f0d48b60aabace9de1e262ccea4322a53
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040375"
---
# <a name="model-your-app39s-architecture"></a>Model aplikacji&#39;architektury s
Aby mieć pewność, że z oprogramowania systemu lub aplikacji spełnia użytkowników potrzebuje, możesz tworzyć modele w programie Visual Studio, jako część opisie ogólną strukturę i zachowanie systemu oprogramowania lub aplikacji. Przy użyciu modeli, może również opisywać wzorców, które są używane w całym projekcie. Modele te ułatwiają zrozumienie istniejącej architektury, omówiono zmiany i wyraźnie komunikacji zamiaru.

 Aby zobaczyć, jakie wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługę wersji narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Cel modelu jest zmniejszenie niejasności, występujących w opisach języka naturalnego, ułatwienie Ty i Twoi współpracownicy wizualizacji projektu i w celu omówienia alternatywnych projektów. Model powinien być używany razem z innych dokumentów lub dyskusji. Przez siebie model nie reprezentuje pełną specyfikację architektury.

> [!NOTE]
>  W tym temacie "system" oznacza, że oprogramowanie, które tworzysz. Może być duży zbiór wielu składników oprogramowania i sprzętu, lub pojedynczej aplikacji lub jej część aplikacji.

 Architektura systemu można podzielić na dwóch obszarach:

-   [Projektowania wysokiego poziomu](#Structure). Opisuje główne składniki i jak współdziałają ze sobą w celu spełnienia poszczególnych wymagań. Jeśli system jest duża, każdy składnik może mieć własną projektowania wysokiego poziomu, który pokazuje, jak jest zbudowany z mniejszych składników.

-   [Wzorce projektowe](#Patterns) i Konwencji używanych w całym projekty składników. Wzorzec opisuje sposób postępowania w osiąganiu celu programowania. Za pomocą tych samych wzorców w całym projekcie, Twój zespół może zmniejszyć kosztów wprowadzania zmian i tworzenie nowego oprogramowania.

## <a name="Structure"></a> Projektowania wysokiego poziomu
 Projektowania wysokiego poziomu w tym artykule opisano główne składniki systemu i jak współdziałają ze sobą w celu osiągnięcia celów projektowania. Działania na poniższej liście są zaangażowane w opracowywaniu projektowania wysokiego poziomu, ale niekoniecznie w określonej kolejności.

 Jeśli aktualizujesz istniejący kod może zacząć poprzez opisanie główne składniki. Upewnij się, zrozumieć wszelkie zmiany wymagań użytkowników i następnie dodać lub zmodyfikować interakcje między składnikami. Jeśli tworzysz nowy system begin przez opis najważniejszych funkcji potrzeb użytkowników. Następnie zapoznaj się z sekwencji interakcji dla przypadków użycia głównego i następnie konsolidowanie sekwencji do projektu składnika.

 W każdym przypadku jest przydatne do tworzenia różnych działań równoległych i tworzenie kodu i testów na wczesnym etapie. Należy unikać próby wykonaj jedną z tych aspektów, przed rozpoczęciem korzystania z innej. Zazwyczaj wymagania i zrozumieć, najlepszym sposobem na projektowanie systemu zmieni się podczas pisania i testowania kodu. W związku z tym należy rozpocząć poprzez zrozumienie i kodowania najważniejszych funkcji, wymagań i projektu. Wypełnij szczegóły w późniejszej iteracji projektu.

-   [Opis wymagań](#Requirements). Punkt początkowy dowolnego projektu jest jasne zrozumienie potrzeb użytkowników.

-   [Wzorce architektury](#BigDecisions). Opcje wprowadzone o podstawowych technologii i architektury elementów systemu.

-   Model danych składników i interfejsy. Możesz narysować diagramy klas do opisania informacje, które jest przekazywane między składnikami, a następnie przechowywane wewnątrz składników.

## <a name="Requirements"></a> Omówienie wymagań
 Ogólny projekt kompletnej aplikacji jest najbardziej efektywne opracowany wraz z modelem wymagania lub innych opis potrzeb użytkowników. Aby uzyskać więcej informacji na temat modeli wymagania, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).

 Jeśli system, który tworzysz składnik w systemie większe, część lub całość wymagań może zostać zawarte w interfejsów programistycznych.

 Model wymagań zapewnia tych podstawowych rodzajów informacji:

- Interfejs dostarczany. Interfejs dostarczany zawiera listę usług lub operacji, które system lub składnika, musisz podać swoim użytkownikom, czy są one ludzi użytkowników ani innych składników oprogramowania.

- Wymagane interfejsy. Interfejs wymagany zawiera listę usług lub operacji, które można użyć systemu lub składnika. W niektórych przypadkach można zaprojektować wszystkie te usługi w ramach własnego systemu. W innych przypadkach zwłaszcza wtedy, gdy projektujesz składnik, który może być łączone z innymi składnikami w wielu konfiguracjach wymaganego interfejsu zostaną ustawione przez zewnętrzne zagadnienia.

- Jakość wymagań dotyczących usług. Wydajności, bezpieczeństwa, niezawodności, a inne cele i ograniczenia, które muszą spełniać system.

  Modelu wymagań są zapisywane z punktu widzenia użytkowników w systemie, czy są one osób lub innymi składnikami oprogramowania. Nie wiedzą niczego wewnętrzne działanie systemu. Z drugiej strony w modelu architektury jest do opisywania wewnętrzne działanie i pokazują, jak spełniają użytkowników potrzebuje.

  Oddzieleniu wymagań i modeli architektury jest przydatne, ponieważ ułatwia celu omówienia ich wymagań z użytkownikami. Pomaga również Refaktoryzuj projektu i należy wziąć pod uwagę alternatywnych architektury podczas przechowywania wymagania bez zmian.

  Ilość szczegółów, które należy umieścić w wymagania lub architektury model zależy od tego, skali projektu oraz wielkość i stopień rozproszenia zespołu. Małego zespołu nad projektem krótki mogą zostać przekazane żadne dodatkowe niż powstawać diagramu klas koncepcji biznesowych i niektórych wzorców projektowych; duży projekt rozproszone na więcej niż jeden region należałoby znacznie bardziej szczegółowo.

## <a name="BigDecisions"></a> Wzorce architektury
 Na wczesnym etapie projektowania należy wybrać technologie główne i elementów, od których zależy od projektu. Obszary, w których należy te opcje są następujące:

- Podstawowa Wybór technologii, takich jak wybrać między bazą danych i systemu plików i wybór między aplikację sieciową i klienta sieci web i tak dalej.

- Opcje struktury, takie jak wybór między Windows Workflow Foundation lub ADO.NET Entity Framework.

- Wybór metody integracji na przykład między usługi enterprise service bus lub kanał point-to-point.

  Te opcje są często określane przez jakości wymagań, takie jak skalowalność i elastyczność i wprowadzenia szczegółowe wymagania są znane. W dużym systemie konfiguracji sprzętu i oprogramowania są silnie powiązane ze sobą.

  Wybrane opcje, które wpływają na sposób używania i interpretować architektury model. Na przykład w systemie, który korzysta z bazy danych, skojarzenia na diagramie klasy może reprezentować relacji lub klucze obce w bazie danych, natomiast w systemie, który jest oparty na plikach XML, skojarzenia może wskazywać odsyłaczy, które używają języka XPath. W rozproszonym systemie wiadomości w diagramie sekwencji może reprezentować komunikatów o komunikacji sieciowej; w przypadku aplikacji niezależna reprezentują wywołania funkcji.

## <a name="Patterns"></a> Wzorce projektowe
 Wzorzec projektowy jest konspektu sposobu projektowania danego aspekt tego oprogramowania, zwłaszcza taki, który występuje w różnych częściach systemu. Przyjmując jednolite podejście w projekcie, można zmniejszyć koszt projektu, zapewnienia spójności interfejsu użytkownika i zmniejszyć koszt zrozumienie i zmieniania kodu.

 Niektóre wzorce projektowe ogólnych, takich jak obserwatora są dobrze znane i powszechnie stosowane. Ponadto są wzorce, które mają zastosowanie tylko do projektu. Na przykład w sieci web system sprzedaży, nastąpi kilka operacji w kodzie gdzie zmian zamówienia klienta. W celu zapewnienia, że był wyświetlany stan zamówienia na każdym etapie, wszystkie czynności należy wykonać konkretnego protokołu aktualizacji bazy danych.

 Część pracy architektury oprogramowania ma na celu określenie, jakie wzorce powinny być przyjęte przez projekt. Jest to zazwyczaj bieżące zadanie, ponieważ nowe wzorce i ulepszenia istniejących wzorców zostaną odnalezione w miarę postępów projektu. Jest to przydatne do organizowania plan rozwoju, tak aby wykonywania wszystkich Twoich wzorców projektowania główne na wczesnym etapie.

 Większość wzorców projektowych może częściowo zawarte w kodzie framework. Część wzorca można zmniejszyć żądania dla deweloperów do użycia z określonymi klasami lub składniki, takie jak warstwa dostępu do bazy danych, które zapewnia, że baza danych odbywa się poprawnie.

 Wzorzec projektowy jest opisane w dokumencie i zwykle obejmuje następujące elementy:

-   Nazwa.

-   Opis kontekst, w której ma zastosowanie. Jakie kryteria należy upewnić się deweloperem, należy rozważyć stosowanie tego wzorca?

-   Krótki opis problemów, które ona rozwiązuje.

-   Model głównych składników oraz ich wzajemne relacje. Może to być klasy lub składniki i interfejsy, za pomocą skojarzeń i zależności między nimi. Elementy zazwyczaj można podzielić na dwie kategorie:

-   Konwencje nazewnictwa.

-   Opis sposobu wzorzec rozwiązuje problem.

-   Opis zmian, które deweloperzy mogą mieć możliwość przyjęcia.

## <a name="see-also"></a>Zobacz też

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)