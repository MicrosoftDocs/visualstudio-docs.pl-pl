---
title: Modelowanie architektury&#39;aplikacji
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e87759206f6d05267e2be5be25fdb8c3e9b70df
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747536"
---
# <a name="model-your-app39s-architecture"></a>Modelowanie architektury&#39;aplikacji
Aby zapewnić, że system oprogramowania lub aplikacja spełnia potrzeby użytkowników, możesz tworzyć modele w programie Visual Studio jako część opisu ogólnej struktury i zachowania systemu oprogramowania lub aplikacji. Korzystając z modeli, można również opisać wzorce, które są używane w całym projekcie. Te modele pomagają zrozumieć istniejącą architekturę, omawiać zmiany i informować o zamiarach jasno.

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Celem modelu jest zredukowanie niejasnościych w opisach języka naturalnego i ułatwienie współpracownikom oraz wizualizacji projektu i omówienia alternatywnych projektów. Model powinien być używany razem z innymi dokumentami lub dyskusjami. Sam model nie reprezentuje kompletnej specyfikacji architektury.

> [!NOTE]
> W tym temacie "system" oznacza opracowywane oprogramowanie. Może to być duża kolekcja wielu składników oprogramowania i sprzętu albo jedna aplikacja lub część aplikacji.

 Architekturę systemu można podzielić na dwa obszary:

- [Projektowanie wysokiego poziomu](#Structure). Opisano w nim główne składniki i sposób współdziałania ze sobą, aby spełnić każde wymaganie. Jeśli system jest duży, każdy składnik może mieć własny projekt wysokiego poziomu, który pokazuje, jak składa się z mniejszych składników.

- [Wzorce projektowe](#Patterns) i konwencje używane w całym projekcie składników programu. Wzorzec opisuje konkretne podejście do osiągnięcia celów programistycznych. Korzystając z tych samych wzorców w całym projekcie, zespół może zmniejszyć koszty dokonywania zmian i tworzenia nowego oprogramowania.

## <a name="Structure"></a>Projektowanie wysokiego poziomu
 Projekt wysokiego poziomu opisuje główne składniki systemu i sposób współdziałania ze sobą, aby osiągnąć cele projektu. Działania na poniższej liście są związane z tworzeniem projektu wysokiego poziomu, chociaż niekoniecznie w określonej kolejności.

 Jeśli aktualizujesz istniejący kod, możesz zacząć od opisywania głównych składników. Upewnij się, że rozumiesz wszelkie zmiany wymagań użytkownika, a następnie Dodaj lub zmodyfikuj interakcje między składnikami. Jeśli tworzysz nowy system, Zacznij od poznania głównych funkcji potrzeb użytkowników. Następnie można zbadać sekwencje interakcji dla głównych przypadków użycia, a następnie skonsolidować sekwencje w projekcie składnika.

 W każdym przypadku warto opracować różne działania równolegle oraz opracować kod i testy na wczesnym etapie. Unikaj próby wykonania jednego z tych aspektów przed rozpoczęciem kolejnego. Zwykle wymagania i zrozumienie najlepszego sposobu projektowania systemu zmienią się podczas pisania i testowania kodu. W związku z tym należy zacząć od ustalenia i kodowania głównych funkcji wymagań i projektu. Wprowadź szczegóły w kolejnych iteracjach projektu.

- [Informacje o wymaganiach](#Requirements). Punktem początkowym dowolnego projektu jest jasne zrozumienie potrzeb użytkowników.

- [Wzorce architektury](#BigDecisions). Opcje dotyczące podstawowych technologii i elementów architektonicznych systemu.

- Model danych składników i interfejsów. Można rysować diagramy klas, aby opisać informacje przesyłane między składnikami i przechowywane w składnikach.

## <a name="Requirements"></a>Informacje o wymaganiach
 Ogólny projekt kompletnej aplikacji jest najwydajniejszie opracowany z modelem wymagań lub innym opisem potrzeb użytkowników. Aby uzyskać więcej informacji na temat modeli wymagań, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

 Jeśli opracowywany system jest składnikiem większego systemu, część lub wszystkie wymagania mogą być zawarte w interfejsach programistycznych.

 Model wymagań zawiera następujące podstawowe informacje:

- Udostępnione interfejsy. Udostępniony interfejs zawiera listę usług lub operacji, które system lub składnik musi dostarczyć swoim użytkownikom, niezależnie od tego, czy są one użytkownikami ludzkimi, czy innymi składnikami oprogramowania.

- Wymagane interfejsy. Wymagany interfejs zawiera listę usług lub operacji, które mogą być używane przez system lub składnik. W niektórych przypadkach będzie można zaprojektować wszystkie te usługi w ramach własnego systemu. W innych przypadkach, szczególnie w przypadku projektowania składnika, który można połączyć z innymi składnikami w wielu konfiguracjach, wymagany interfejs zostanie ustawiony przez zagadnienia zewnętrzne.

- Wymagania dotyczące jakości usług. Wydajność, bezpieczeństwo, niezawodność i inne cele oraz ograniczenia, które system musi spełnić.

  Model wymagań jest zapisywana z punktu widzenia użytkowników systemu, niezależnie od tego, czy są one osobami, czy innymi składnikami oprogramowania. Nie znają nic z wewnętrznych działań systemu. Z drugiej strony celem w modelu architektury jest opisywanie pracy wewnętrznej i pokazanie, jak spełnią się potrzeby użytkowników.

  Wymagania i różne modele architektoniczne są przydatne, ponieważ ułatwiają one przedyskutowanie wymagań z użytkownikami. Ułatwia również refaktoryzację projektu i rozważenie alternatywnych architektur przy zachowaniu niezmienionych wymagań.

  Ilość szczegółów, które należy umieścić w wymaganiach lub modelu architektury, zależy od skali projektu oraz wielkości i dystrybucji zespołu. Niewielki zespół w krótkim projekcie może nie przekroczyć szkicu diagramu klas koncepcji firmy i niektórych wzorców projektowych; duży projekt dystrybuowany przez więcej niż jeden region będzie wymagał znacznie większej szczegółowości.

## <a name="BigDecisions"></a>Wzorce architektury
 Na wczesnym etapie opracowywania należy wybrać główne technologie i elementy, od których zależy projekt. Obszary, w których należy dokonać wyboru, obejmują następujące elementy:

- Podstawowe opcje technologii, takie jak wybór między bazą danych i systemem plików oraz wybór między aplikacją sieciową a klientem internetowym itd.

- Opcje struktur, takie jak wybór między Windows Workflow Foundation lub ADO.NET Entity Framework.

- Wybór metody integracji, na przykład między usługą Service Bus lub kanałem punkt-punkt.

  Te opcje są często określane przez wymagania dotyczące jakości usług, takie jak skalowanie i elastyczność, i można je wprowadzić przed ustaleniem szczegółowych wymagań. W dużym systemie konfiguracja sprzętu i oprogramowania jest silnie powiązana.

  Wybrane opcje mają wpływ na sposób użycia i interpretacji modelu architektury. Na przykład w systemie, który korzysta z bazy danych, skojarzenia w diagramie klas mogą reprezentować relacje lub klucze obce w bazie danych, natomiast w systemie, który jest oparty na plikach XML, skojarzenia mogą wskazywać odwołania krzyżowe, które używają XPath. W systemie rozproszonym komunikaty w diagramie sekwencji mogą reprezentować komunikaty w sieci przewodowej. w aplikacji samodzielnej mogą one reprezentować wywołania funkcji.

## <a name="Patterns"></a>Wzorce projektowe
 Wzorzec projektowy to zarys sposobu projektowania określonego aspektu oprogramowania, szczególnie te, które odnoszą się do różnych części systemu. Przyjmując jednolite podejście w całym projekcie, można zmniejszyć koszt projektu, zapewnić spójność w interfejsie użytkownika, a także zmniejszyć koszt interpretacji i zmiany kodu.

 Niektóre ogólne wzorce projektowe, takie jak obserwator, są dobrze znane i szeroko stosowane. Ponadto istnieją wzorce, które mają zastosowanie tylko do projektu. Na przykład w systemie sprzedaży sieci Web będzie kilka operacji w kodzie, w którym zmiany są wprowadzane do zamówienia klienta. Aby upewnić się, że stan zamówienia jest dokładnie wyświetlany na każdym etapie, wszystkie te operacje muszą być zgodne z określonym protokołem w celu zaktualizowania bazy danych.

 Część pracy z architekturą oprogramowania polega na określeniu, jakie wzorce należy przyjąć w ramach projektu. Zwykle jest to bieżące zadanie, ponieważ nowe wzorce i ulepszenia istniejących wzorców zostaną odnalezione jako postęp projektu. Warto zorganizować plan rozwoju w taki sposób, aby wykonywał wszystkie główne wzorce projektowe na wczesnym etapie.

 Większość wzorców projektowych może być częściowo pomieścić w kodzie struktury. Część wzorca może zostać zredukowana, aby wymagać od programisty używania określonych klas lub składników, takich jak Warstwa dostępu do bazy danych, która gwarantuje, że baza danych jest prawidłowo obsługiwana.

 Wzorzec projektowy został opisany w dokumencie i zwykle zawiera te części:

- Nazwij.

- Opis kontekstu, w którym ma zastosowanie. Jakie kryteria należy wziąć pod uwagę w przypadku zastosowania tego wzorca przez dewelopera?

- Krótkie wyjaśnienie problemu, który rozwiązuje.

- Model głównych części i ich relacji. Mogą to być klasy lub składniki i interfejsy, ze skojarzeniami i zależnościami między nimi. Elementy zwykle należą do dwóch kategorii:

- Konwencje nazewnictwa.

- Opis sposobu, w jaki wzorzec rozwiązuje problem.

- Opis wariantów, które mogą być w stanie zastosować deweloperzy.

## <a name="see-also"></a>Zobacz także

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)