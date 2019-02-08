---
title: Wymagania modelu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cda0284bd9ae4b0f68a8bb0fa779959f52650bdd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937360"
---
# <a name="model-user-requirements"></a>Wymagania modelu użytkownika

Program Visual Studio pozwala zrozumieć, omówienia i komunikują się potrzeby użytkowników, rysując diagramy dotyczące ich działania i część systemu jest odtwarzany w pozwala im to osiągnąć swoje cele. Modelu wymagań to zbiór tych diagramów, z których każdy koncentruje się na inny aspekt potrzeb użytkowników. Aby uzyskać demonstracyjne wideo – zobacz: [Modelowanie domeny biznesowej](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

Aby zobaczyć, które wersje programu Visual Studio obsługuje każdy typ modelu, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Wymagania modelu pomoże Ci:

- Skup się na zachowaniu zewnętrznego systemu, niezależnie od jego wewnętrzną konstrukcją.

- Opis użytkowników i udziałowców wymaga o wiele mniej niejednoznaczności niż w języku naturalnym.

- Zdefiniuj spójne słownik terminów, używane przez użytkowników, deweloperów i testerów.

- Ogranicz luki i niespójności w wymaganiach.

- Zmniejsz czynności niezbędne do reagowania na zmiany wymagań.

- Zaplanuj kolejność, w którym będą opracowywane funkcje.

- Na użytek modele jako podstawa testy systemu, co wyczyść relację między testy i wymagania. Gdy zmienią się wymagania tę relację pomaga poprawnie zaktualizować testy. To sprawia, że się, że system spełnia nowe wymagania.

Modelu wymagań zapewnia największe korzyści, jeśli go użyć do dyskusji fokus z użytkowników lub ich przedstawicieli, a go ponownie na początku każdej iteracji. Nie masz Oznacz go jako ukończony szczegółowo przed napisaniem kodu. Częściowo działającą aplikację, nawet wtedy, gdy znacznie uproszczone, zazwyczaj są podstawą najbardziej pobudzania dyskusję na temat wymagań użytkowników. Model jest efektywny sposób podsumowywania wyniki tych dyskusji. Aby uzyskać więcej informacji, zobacz [używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> W tych tematach "system" oznacza system lub aplikację, którą tworzysz. Może być duży zbiór wielu składniki sprzętu i oprogramowania; lub pojedynczej aplikacji; lub składnik oprogramowania w systemie większe. W każdym przypadku modelu wymagań w tym artykule opisano zachowanie, które nie jest widoczny spoza systemu, czy za pośrednictwem interfejsu użytkownika lub interfejsu API.

## <a name="common-tasks"></a>Wspólne zadania

Można utworzyć kilka różnych widoków wymagań użytkowników.  Każdy widok zawiera określonego typu informacji.  Podczas tworzenia tych widoków, najlepiej jest często przenieść z jednego do drugiego. Można uruchomić w dowolnym widoku.

|Diagram lub dokumentu|Znaczenie w modelu wymagań|Sekcja|
|-|-|-|
|Diagram koncepcyjny klas|Słownik typów, które są używane do opisywania wymagania dotyczące programu typy widoczne w interfejsie systemu.||
|Dodatkowe dokumenty lub elementy robocze|Kryteria wydajności, bezpieczeństwa, użyteczność i niezawodność.|[Opisujące jakości wymagań](#QoSRequirements)|
|Dodatkowe dokumenty lub elementy robocze|Ograniczenia i reguły nie jest specyficzne dla danego przypadku użycia|[Wyświetlanie reguły biznesowe](#BusinessRules)|

Należy zauważyć, że większość typów diagram może służyć do innych celów. Omówienie typów na diagramie, zobacz [tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md).

##  <a name="BusinessRules"></a> Wyświetlanie reguły biznesowe

Reguły biznesowej jest wymagana, która nie jest skojarzony z konkretnego przypadku użycia, należy przestrzegać w całym systemie.

Wiele reguł biznesowych są ograniczenia relacje klas pojęć. Można napisać te *reguły biznesowe statyczne* jako komentarze skojarzone z odpowiednich klas na diagramie klasy pojęć. Na przykład:

![Reguła w komentarzu dołączona do klasy zamówienia.](../modeling/media/uml_reqmcd2.png)

*Reguły biznesowe dynamiczne* ograniczyć dozwolone sekwencja zdarzeń. Na przykład używasz diagramie sekwencji lub działania, aby pokazać, że użytkownik musi zalogować się przed przystąpieniem do wykonywania innych operacji w systemie.

Jednak wiele dynamiczne reguły może być bardziej efektywne i objęty wyrażona przez zamianę statyczne reguły. Na przykład można dodać atrybutu logicznego rejestrowane w do klasy w model koncepcyjny klasy. Czy dodatek rejestrowane jako postcondition dziennika w przypadku użycia, a następnie dodaj go jako warunek wstępny do większości innych przypadków użycia. Takie podejście umożliwia Unikaj definiowania wszystkich możliwych kombinacji sekwencja zdarzeń. Jest również bardziej elastyczne, gdy trzeba dodać nowych przypadków użycia w modelu.

Należy zauważyć, że w tym miejscu to o sposób definiowania wymagań i jest niezależne od sposobu implementacji wymagania w kodzie programu.

Więcej informacji można znaleźć w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|-|-|
|Jak tworzyć kod, który działa zgodnie z regułami biznesowymi|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

##  <a name="QoSRequirements"></a> Opisujące jakości wymagań

Istnieje kilka kategorii wymagań dotyczących jakości usługi. Ulepszenia obejmują następujące czynności:

-   Wydajność

-   Zabezpieczenia

-   Użyteczność

-   Niezawodność

-   Niezawodność

Niektóre z tych wymagań można uwzględnić w opisach przypadki użycia określonego. Inne wymagania nie są specyficzne dla przypadków użycia i najbardziej efektywne są zapisywane w osobnym dokumencie. Możliwe, to warto stosować się do słownictwa zdefiniowane za pomocą modelu wymagań. W poniższym przykładzie należy zauważyć, że głównym słowa używane wymaganie są tytuły aktorów, przypadki użycia i klas w poprzedniej ilustracji:

Jeśli restauracji usunie element Menu, gdy klient jest zamawianie posiłku, dowolny element zamówienia, który odwołuje się do tego elementu Menu będą wyświetlane w kolorze czerwonym.

Zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md) Aby dowiedzieć się, jak tworzyć kod, który jest zgodna z jakością wymagania dotyczące usługi.

## <a name="see-also"></a>Zobacz także

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
