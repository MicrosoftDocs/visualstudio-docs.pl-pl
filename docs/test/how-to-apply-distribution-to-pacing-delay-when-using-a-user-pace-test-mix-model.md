---
title: Zastosuj dystrybucję do opóźnienia tempa podczas testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 953c1ac4cb6e0f87d2a36080cc751ea26f66d63e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114492"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Jak: Stosowanie dystrybucji do opóźnienia tempa dla modelu mix testu tempa użytkownika

Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążenia**można użyć Edytora testów obciążenia, aby zmienić właściwości scenariusza, aby spełnić twoje potrzeby i cele testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Właściwość **Zastosuj dystrybucję do opóźnienia tempa** jest ustawiana przy użyciu okna **Właściwości.** Właściwości scenariusza testu obciążenia są modyfikowane przy użyciu Edytora testów obciążenia.

> [!NOTE]
> **Właściwość Zastosuj dystrybucję do opóźnienia tempa** ma zastosowanie tylko wtedy, gdy *mix testu obciążenia* jest skonfigurowany na podstawie tempa użytkownika. Aby uzyskać więcej informacji, zobacz [Edytowanie modeli miksu tekstu, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

Wartość opóźnienia **rozsyłania dystrybucji do pacingu** można ustawić na wartość true lub false:

- **Prawda:** Scenariusz stosuje normalne opóźnienia dystrybucji statystycznej, które są określone przez wartość w **testach na godzinę** kolumny w oknie dialogowym **Edycja miksu testowego.** Aby uzyskać więcej informacji, zobacz [Edytowanie modeli miksu tekstu, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartość w oknie dialogowym **Edytowanie miksu testowego** dla zestawu testów do dwóch użytkowników na godzinę. Jeśli **zastosuj dystrybucję do pacing delay** właściwość jest ustawiona na **True**, normalny rozkład statystyczny jest stosowany do czasu oczekiwania między testami. Testy będą nadal uruchamiać dwa testy na godzinę, ale niekoniecznie będzie to 30-minutowe opóźnienie między nimi. Pierwszy test może przebiegać po czterech minutach, a drugi po 45 minutach.

- **False:** Testy są uruchamiane w tempie określonym dla wartości w kolumnie **Testy na użytkownika na godzinę** w oknie dialogowym **Edytowanie miksu testowego.** Aby uzyskać więcej informacji, zobacz [Edytowanie modeli miksu tekstu, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartość w oknie dialogowym **Edytowanie miksu testowego** dla zestawu testów do dwóch użytkowników na godzinę. Jeśli **Zastosuj dystrybucji do pacing delay** właściwość jest **ustawiona**na False , nie daje swobody podczas uruchamiania testów. Test będzie uruchamiany co 30 minut. To upewnia się, że można wykonać dwa testy na godzinę.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Aby określić ustawienie właściwości Zastosuj dystrybucję do opóźnienia tempa dla scenariusza

1. Otwórz test obciążenia.

   Pojawi się **Edytor testów obciążenia.** Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **Scenariusze** drzewa testu obciążenia wybierz węzeł scenariusza, do którego chcesz zastosować rozkład pacingu.

3. W menu **Widok** wybierz polecenie **Okno Właściwości**.

   Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości.**

4. W wartości właściwości **dla zastosuj dystrybucję do opóźnienia pacingu**wybierz opcję **Prawda** lub **Fałsz**.

5. Wybierz pozycję**Zapisz** **plik** > . Teraz można uruchomić test obciążenia z nową **zastosuj dystrybucję do pacing delay** wartość.

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
