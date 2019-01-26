---
title: Określanie agentów testowych do użycia w scenariuszach testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: ef1325fbe568e82f03d694523a4580f2d61265c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966741"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Instrukcje: Określanie agentów testowych do użycia w scenariuszach testów obciążenia

Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości scenariuszy do spełnienia potrzeb i celów testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

Agenci są określane za pomocą **edytora testu obciążenia** zmienić **agenci do użycia** właściwość **właściwości** okna.

Możesz określić agentów, które mają używać, jeśli za pomocą kontrolerów i agentów, aby uruchomić ładowanie testowanie zdalne za pomocą dany scenariusz. Na przykład można określić konkretny zestaw agentów, aby zachować spójność podczas analizowania trendów wydajności. Ponadto agentów może być rozproszonej geograficznie, tak, że istnieje koligacja między skryptami, zakres ich działania i w którym znajduje się agent.

> [!TIP]
> Zamiast fizycznie umieszczenie agenta do lokacji zdalnej, innym rozwiązaniem jest użycie emulacji sieci emulować wolną sieć. Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Inną przyczyną jest fakt, że niektóre, ale nie wszystkich agentów może mieć zainstalowanego na nich oprogramowania, który jest wymagany dla danego scenariusza.

Można kontrolować wybór agenta dla danego testu przy użyciu ról w ustawieniach testu. Aby uzyskać więcej informacji, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

Jeśli komputer agenta testowego ma więcej niż 75 procent wykorzystania procesora CPU lub ma mniej niż 10% dostępnej pamięci fizycznej Dodaj więcej agentów do testu obciążeniowego, aby upewnić się, że komputer agenta nie utknie w teście obciążenia.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Aby określić agentów na potrzeby scenariusza

1.  Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2.  Obciążenia test drzew **scenariuszy** folderu, wybierz węzeł scenariusz, dla którego chcesz określić agentów do użytku.

3.  Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w **właściwości** okna.

4.  W polu tekstowym dla **agenci do użycia** właściwości, wpisz listę agentów, na których może uruchomić scenariusza.

     Agenci muszą być rozdzielone przecinkami, na przykład "**agenta agenta 1, agenta 2, 3**". Niewypełnienie tej właściwości oznacza, że scenariusz powinien wykorzystywać wszystkich dostępnych agentów.

    > [!NOTE]
    > **Agenci do użycia** właściwość jest ignorowana dla przebiegów lokalnych. Dla przebiegów zdalnych, jeśli żaden z agentów, określone w **agenci do użycia** istnieje, nie zostaną uruchomione testy, w tym scenariuszu.

5.  Po zmianie właściwości wybierz **Zapisz** na **pliku** menu. Następnie można uruchomić testu obciążenia za pomocą nowego **agenci do użycia** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)