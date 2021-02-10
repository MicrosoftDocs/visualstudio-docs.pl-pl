---
title: Wymagania modelu użytkownika
description: Dowiedz się, w jaki sposób program Visual Studio pomaga zrozumieć, omówić i komunikować się z potrzebami użytkowników, rysując diagramy związane z ich działaniami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d55e549d2dccdc047cbf4449392cc090a569f85c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970585"
---
# <a name="model-user-requirements"></a>Wymagania modelu użytkownika

Program Visual Studio pomaga zrozumieć, omówić i komunikować się z potrzebami użytkowników, rysując diagramy związane z ich działaniami i część, która jest odtwarzana przez system w celu ułatwienia im osiągnięcia celów. Model wymagań to zbiór tych diagramów, z których każdy koncentruje się na różnych aspektach potrzeb użytkowników. Aby zapoznać się z prezentacją, zobacz: [modelowanie domeny biznesowej](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

Aby sprawdzić, które wersje programu Visual Studio obsługują każdy typ modelu, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Model wymagań ułatwia:

- Skup się na zewnętrznym zachowaniu systemu, niezależnie od jego wewnętrznego projektu.

- Opisz potrzeby użytkowników i uczestników projektu o znacznie mniejszej niejednoznaczności niż w języku naturalnym.

- Zdefiniuj spójny słownik terminów, które mogą być używane przez użytkowników, deweloperów i testerów.

- Ogranicz luki i niespójności w wymaganiach.

- Zmniejsz ilość pracy wymaganej do reagowania na zmiany wymagań.

- Zaplanuj kolejność, w której będą rozwijane funkcje.

- Używaj modeli jako podstawy dla testów systemowych, co powoduje wyraźną relację między testami i wymaganiami. Po zmianie wymagań ta relacja pomaga zaktualizować testy prawidłowo. Pozwala to upewnić się, że system spełnia nowe wymagania.

Model wymagań zapewnia największą korzyść, jeśli jest używany do koncentracji dyskusji z użytkownikami lub ich przedstawicielami, a następnie ponownie odwiedzany na początku każdej iteracji. Przed zapisaniem kodu nie jest konieczne jego szczegółowe zakończenie. Częściowo działająca aplikacja, nawet jeśli bardzo uproszczone, zazwyczaj stanowi najbardziej stymulowaną podstawę do omówienia wymagań dla użytkowników. Model jest efektywnym sposobem podsumowywania wyników dyskusji. Aby uzyskać więcej informacji, zobacz [Używanie modeli w procesie tworzenia oprogramowania](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> W tych tematach "system" oznacza system lub aplikację, którą tworzysz. Może to być duża kolekcja wielu składników oprogramowania i sprzętu. lub pojedynczej aplikacji; lub składnika oprogramowania w większym systemie. W każdym przypadku model wymagań opisuje zachowanie widoczne spoza systemu, niezależnie od tego, czy za pośrednictwem interfejsu użytkownika, czy interfejsu API.

## <a name="common-tasks"></a>Typowe zadania

Można utworzyć kilka różnych widoków wymagań użytkowników.  Każdy widok zawiera informacje określonego typu.  Podczas tworzenia tych widoków najlepiej jest przebiegać często od jednego do drugiego. Możesz rozpocząć od dowolnego widoku.

|Diagram lub dokument|Co opisano w modelu wymagań|Sekcja|
|-|-|-|
|Diagram klasy koncepcyjnej|Słownik typów, które są używane do opisywania wymagań; typy widoczne w interfejsie systemu.||
|Dodatkowe dokumenty lub elementy robocze|Kryteria wydajności, bezpieczeństwa, użyteczności i niezawodności.|[Opisywanie wymagań dotyczących jakości usług](#QoSRequirements)|
|Dodatkowe dokumenty lub elementy robocze|Ograniczenia i reguły niespecyficzne dla określonego przypadku użycia|[Wyświetlanie reguł firmy](#BusinessRules)|

Należy zauważyć, że większość typów diagramów może być używana do innych celów. Aby zapoznać się z omówieniem typów diagramów, zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md).

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Wyświetlanie reguł firmy

Reguła biznesowa jest wymagana, która nie jest skojarzona z konkretnym przypadkiem użycia i powinna być zastosowana w całym systemie.

Wiele reguł biznesowych to ograniczenia dotyczące relacji między klasami koncepcyjnymi. Te *statyczne reguły biznesowe* można napisać jako komentarze skojarzone z odpowiednimi klasami na diagramie klasy koncepcyjnej. Na przykład:

![Reguła w komentarzu dołączonym do klasy Order.](../modeling/media/uml_reqmcd2.png)

*Dynamiczne reguły biznesowe* ograniczają dozwolone sekwencje zdarzeń. Na przykład można użyć sekwencji lub diagramu aktywności, aby pokazać, że użytkownik musi się zalogować przed wykonaniem innych operacji w systemie.

Jednak wiele reguł dynamicznych może być bardziej wydajnych i ogólnie określonych przez zastępowanie ich regułami statycznymi. Na przykład, można dodać atrybut Boolean "zalogowany" do klasy w modelu klasy koncepcyjnej. Należy dodać zalogowany jako błąd warunku końcowego w przypadku użycia i dodać go jako warunek wstępny większości innych przypadków użycia. Takie podejście pozwala uniknąć definiowania wszystkich możliwych kombinacji sekwencji zdarzeń. Jest to również bardziej elastyczne, gdy trzeba dodać do modelu nowe przypadki użycia.

Należy zauważyć, że w tym miejscu opisano sposób definiowania wymagań oraz to, że jest on niezależny od sposobu implementacji wymagań w kodzie programu.

Dodatkowe informacje znajdują się w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|-|-|
|Jak opracowywać kod zgodny z regułami biznesowymi|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Opisywanie wymagań Quality of Service

Istnieje kilka kategorii wymagań dotyczących jakości usług. Należą do nich następujące elementy:

- Wydajność

- Zabezpieczenia

- Łatwość obsługi

- Niezawodność

- Niezawodność

Niektóre z tych wymagań można uwzględnić w opisach konkretnych przypadków użycia. Inne wymagania nie są specyficzne dla przypadków użycia i są najbardziej efektywnie zapisywane w osobnym dokumencie. Gdy jest to możliwe, warto przestrzegać słownictwa zdefiniowanego przez model wymagań. W poniższym przykładzie należy zauważyć, że główne wyrazy używane w wymaganiu są tytułami aktorów, przypadków użycia i klas na powyższych ilustracjach:

Jeśli restauracji usunie element menu, gdy klient porządkuje posiłk, każdy element zamówienia, który odwołuje się do tego elementu menu będzie wyświetlany na czerwono.

Zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md) , aby dowiedzieć się, jak opracować kod, który jest zgodny z wymaganiami dotyczącymi jakości usług.

## <a name="see-also"></a>Zobacz też

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
