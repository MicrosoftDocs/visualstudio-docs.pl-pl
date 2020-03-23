---
title: Określ agentów testowych do użycia w scenariuszach testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d23d565752d81bff960027090ddaaf88e9d78ed5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588931"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Jak: Określ agentów testowych do użycia w scenariuszach testów obciążenia

Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić właściwości scenariuszy, aby spełnić twoje potrzeby i cele testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisy, zobacz [Właściwości scenariusza testu obciążenia.](../test/load-test-scenario-properties.md)

Agenci są określone za pomocą **Edytora testów obciążenia,** aby zmienić **agentów do użycia** właściwości w oknie **Właściwości.**

Można określić agentów, które mają być używane w scenariuszu, jeśli używasz kontrolerów i agentów do zdalnego uruchamiania testu obciążenia. Na przykład można określić konkretny zestaw agentów, aby zachować spójność podczas analizowania trendów wydajności. Ponadto agenci mogą być geograficznie rozproszone, tak, że istnieje koligacja między skryptami, które uruchamiają i gdzie znajduje się agent.

> [!TIP]
> Inną opcją jest użycie emulacji sieci w celu emulacji powolnej sieci, zamiast fizycznie umieszczać agenta w lokacji zdalnej. Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Aby uzyskać więcej informacji, zobacz [Kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Innym powodem jest to, że niektóre, ale nie wszystkie, agenci mogą mieć zainstalowane oprogramowanie, które jest wymagane dla określonego scenariusza.

Można kontrolować wybór agenta dla danego testu uruchomić przy użyciu ról w ustawieniach testu. Aby uzyskać więcej informacji, zobacz [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

Jeśli maszyna agenta testowego ma więcej niż 75 procent wykorzystania procesora CPU lub ma mniej niż 10 procent pamięci fizycznej dostępne, dodać więcej agentów do testu obciążenia, aby upewnić się, że komputer agenta nie staje się wąskie gardło w teście obciążenia.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Aby określić agentów, które mają być używane dla scenariusza

1. Otwórz test obciążenia.

     Pojawi się **Edytor testów obciążenia.** Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **Scenariusze** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz określić agentów do użycia.

3. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości.**

4. W polu tekstowym dla **agentów do użycia** właściwości wpisz listę agentów, na których scenariusz może działać.

     Agenci muszą być oddzielone przecinkami, na przykład "**Agent1, Agent2, Agent3**". Niewypełnienie tej właściwości oznacza, że scenariusz powinien wykorzystywać wszystkich dostępnych agentów.

    > [!NOTE]
    > **Właściwość Agenci do użycia** jest ignorowana dla przebiegów lokalnych. W przypadku uruchomień zdalnych, jeśli żaden z agentów określonych w **agenty do użycia** istnieje, testy w scenariuszu nie będzie działać.

5. Po zmianie właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowych **agentów do użycia** wartości.

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
