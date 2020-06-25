---
title: Określ agentów testowych do użycia w scenariuszach testów obciążenia
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: 5d9e22200a63544b4539f7bf78c48d5711974776
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287496"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Instrukcje: Określanie agentów testowych do użycia w scenariuszach testów obciążenia

Po utworzeniu testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**można użyć **Edytor testu obciążeniowego** , aby zmienić właściwości scenariuszy, aby spełniały potrzeby testowania i cele.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisów, zobacz [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

Agenci są określeni przy użyciu **Edytor testu obciążeniowego** do zmiany **agentów do użycia** właściwości w oknie **Właściwości** .

Można określić agentów, których scenariusz ma używać, jeśli używasz kontrolerów i agentów do zdalnego uruchamiania testu obciążenia. Na przykład można określić konkretny zestaw agentów, aby zachować spójność podczas analizowania trendów wydajności. Ponadto agenci mogą być geograficznie rozpowszechniane, dzięki czemu istnieje koligacja między uruchomionymi skryptami i miejscem, w którym znajduje się Agent.

> [!TIP]
> Zamiast fizycznego umieszczania agenta w zdalnej lokacji, kolejną opcją jest użycie emulacji sieci do emulowania powolnej sieci. Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Innym powodem jest to, że niektóre, ale nie wszystkie, agenci mogą mieć zainstalowane na nich oprogramowanie, które jest wymagane w konkretnym scenariuszu.

Można kontrolować wybór agenta dla danego przebiegu testowego za pomocą ról w ustawieniach testu. Aby uzyskać więcej informacji, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

Jeśli maszyna testowa ma więcej niż 75 procent użycia procesora CPU lub ma mniej niż 10% dostępnej pamięci fizycznej, Dodaj więcej agentów do testu obciążenia, aby upewnić się, że maszyna agenta nie stanie się wąskim gardłem w teście obciążenia.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Aby określić agentów do użycia w scenariuszu

1. Otwórz test obciążenia.

     Zostanie wyświetlona **Edytor testu obciążeniowego** . Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **scenariuszy** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz określić agentów do użycia.

3. W menu **Widok** wybierz polecenie **okno właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości** .

4. W polu tekstowym dla **agentów do używania** właściwości wpisz listę agentów, na których można uruchomić ten scenariusz.

     Agenci muszą być oddzielone przecinkami, na przykład "**agenta 1, agenta 2, agenta 3**". Niewypełnienie tej właściwości oznacza, że scenariusz powinien wykorzystywać wszystkich dostępnych agentów.

    > [!NOTE]
    > Właściwość **Agents to use** jest ignorowana w przypadku uruchomień lokalnych. W przypadku uruchamiania zdalnego, jeśli żaden z agentów określonych w **agentach** nie zostanie użyty, testy w tym scenariuszu nie zostaną uruchomione.

5. Po zmianie właściwości wybierz pozycję **Zapisz** w menu **plik** . Następnie można uruchomić test obciążenia za pomocą nowych **agentów, aby użyć** wartości.

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
