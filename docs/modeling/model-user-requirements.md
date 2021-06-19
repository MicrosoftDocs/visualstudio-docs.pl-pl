---
title: Wymagania modelu użytkownika
description: Dowiedz się, Visual Studio pomaga zrozumieć, omówić i przekazać potrzeby użytkowników, rysując diagramy dotyczące ich działań.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 381395eb0b9dabde0e94c479cb43033bc8443c8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390154"
---
# <a name="model-user-requirements"></a>Wymagania modelu użytkownika

Visual Studio pomaga zrozumieć, omówić i przekazać potrzeby użytkowników przez rysowanie diagramów dotyczących ich działań i części, która odgrywa przez system w pomaganiu im w osiągnięciu celów. Model wymagań to zestaw tych diagramów, z których każdy koncentruje się na innym aspektie potrzeb użytkowników. Aby uzyskać pokaz wideo, zobacz: [Modeling the Business Domain (Modelowanie domeny biznesowej).](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)

Aby sprawdzić, które wersje Visual Studio obsługują poszczególne typy modelu, zobacz Obsługa wersji dla architektury [i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

Model wymagań ułatwia:

- Skoncentruj się na zachowaniu zewnętrznym systemu, niezależnie od jego wewnętrznego projektu.

- Opisz potrzeby użytkowników i uczestników projektu ze znacznie mniej niejednoznacznością niż w języku naturalnym.

- Zdefiniuj spójny słownik terminów, z których mogą korzystać użytkownicy, deweloperzy i testerzy.

- Zmniejsz luki i niespójności w wymaganiach.

- Zmniejsz ilość pracy potrzebnej do reagowania na zmiany wymagań.

- Zaplanuj kolejność, w jakiej funkcje będą opracowywane.

- Użyj modeli jako podstawy dla testów systemowych, aby uzyskać jasne relacje między testami i wymaganiami. Po zmianie wymagań ta relacja ułatwia poprawne aktualizowanie testów. Dzięki temu system spełnia nowe wymagania.

Model wymagań zapewnia największe korzyści, jeśli użyjemy go do skoncentrowania dyskusji z użytkownikami lub ich przedstawicielami, a następnie do niego ponownie na początku każdej iteracji. Nie trzeba szczegółowo go kończyć przed napisaniem kodu. Częściowo robocza aplikacja, nawet jeśli jest bardzo uproszczona, zazwyczaj stanowi najbardziej najpopularniejszą podstawę do dyskusji o wymaganiach z użytkownikami. Model jest efektywnym sposobem podsumowania wyników tych dyskusji. Aby uzyskać więcej informacji, zobacz Use models in your development process (Korzystanie [z modeli w procesie tworzenia oprogramowania).](../modeling/use-models-in-your-development-process.md)

> [!NOTE]
> W tych tematach "system" oznacza system lub aplikację, które opracowujesz. Może to być duża kolekcja wielu składników oprogramowania i sprzętu; lub pojedynczej aplikacji; lub składnik oprogramowania w większym systemie. W każdym przypadku model wymagań opisuje zachowanie, które jest widoczne spoza systemu, za pośrednictwem interfejsu użytkownika lub interfejsu API.

## <a name="common-tasks"></a>Typowe zadania

Można utworzyć kilka różnych widoków wymagań użytkowników.  Każdy widok zawiera określony typ informacji.  Podczas tworzenia tych widoków najlepiej jest często przechodzić z jednego do drugiego. Możesz rozpocząć od dowolnego widoku.

|Diagram lub dokument|Opis w modelu wymagań|Sekcja|
|-|-|-|
|Diagram klas koncepcyjnych|Słownik typów używanych do opisywania wymagań; typy widoczne w interfejsie systemu.||
|Dodatkowe dokumenty lub elementy robocze|Kryteria wydajności, zabezpieczeń, użyteczności i niezawodności.|[Opisywanie jakości wymagań dotyczących usługi](#QoSRequirements)|
|Dodatkowe dokumenty lub elementy robocze|Ograniczenia i reguły, które nie są specyficzne dla konkretnego przypadku użycia|[Wyświetlanie reguł biznesowych](#BusinessRules)|

Zwróć uwagę, że większość typów diagramów może być używana do innych celów. Aby uzyskać omówienie typów diagramów, zobacz Create models for your app (Tworzenie [modeli dla aplikacji).](../modeling/create-models-for-your-app.md)

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Wyświetlane Business Rules

Reguła biznesowa jest wymaganiem, które nie jest skojarzone z konkretnym przypadekem użycia i powinno być przestrzegane w całym systemie.

Wiele reguł biznesowych to ograniczenia dotyczące relacji między klasami koncepcyjnych. Te statyczne reguły *biznesowe* można napisać jako komentarze skojarzone z odpowiednimi klasami na diagramie klas koncepcyjnych. Na przykład:

![Reguła w komentarzu dołączonym do klasy Order.](../modeling/media/uml_reqmcd2.png)

*Dynamiczne reguły biznesowe* ograniczają dopuszczalne sekwencje zdarzeń. Można na przykład użyć sekwencji lub diagramu aktywności, aby pokazać, że użytkownik musi się zalogować przed wykonaniem innych operacji w systemie.

Jednak wiele reguł dynamicznych może być efektywniej i ogólnie określonych przez zastąpienie ich reguł statycznych. Na przykład można dodać atrybut logiczny "Zalogowano" do klasy w koncepcyjnym modelu klas. Należy dodać pozycję Zalogowano jako postcondition przypadku użycia logowania i dodać ją jako warunek wstępny większości innych przypadków użycia. Takie podejście pozwala uniknąć definiowania wszystkich możliwych kombinacji sekwencji zdarzeń. Jest ona również bardziej elastyczna, gdy trzeba dodać nowe przypadki użycia do modelu.

Należy zauważyć, że wybór w tym miejscu dotyczy sposobu definiowania wymagań i jest on niezależny od sposobu implementacji wymagań w kodzie programu.

Więcej informacji można znaleźć w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|-|-|
|Tworzenie kodu zgodnego z regułami biznesowymi|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Opisywanie Quality of Service wymagań

Istnieje kilka kategorii wymagań w zakresie jakości usług. Obejmują one następujące elementy:

- Wydajność

- Zabezpieczenia

- Łatwość obsługi

- Niezawodność

- Niezawodność

Niektóre z tych wymagań można uwzględnić w opisach konkretnych przypadków użycia. Inne wymagania nie są specyficzne dla przypadków użycia i najskuteczniej są zapisywane w oddzielnym dokumencie. Gdy jest to możliwe, warto stosować się do słownictwa zdefiniowanego przez model wymagań. W poniższym przykładzie zwróć uwagę, że głównymi wyrazami używanymi w wymaganiu są tytuły aktorów, przypadków użycia i klas na poprzednich ilustracjach:

Jeśli restauracji usunie element menu, gdy klient zamówi jedzenie, dowolny element zamówienia, który odwołuje się do tego elementu menu, zostanie wyświetlony na czerwono.

Zobacz [Modelowanie architektury aplikacji,](../modeling/model-your-app-s-architecture.md) aby dowiedzieć się, jak opracowywać kod zgodny z wymaganiami w zakresie jakości usług.

## <a name="see-also"></a>Zobacz też

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
