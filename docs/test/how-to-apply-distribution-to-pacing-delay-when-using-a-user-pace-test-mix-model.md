---
title: Zastosuj do rozkład opóźnienia do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 758e07ba6fae2d06d72f9a2df98a2e78b6e2284a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917929"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Instrukcje: Zastosuj rozkład do opóźnienia dla użytkownika w tempie model testu mieszanego do

Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążeniowego**, można użyć edytora testu obciążenia, aby zmienić właściwości scenariuszy do spełnienia potrzeb i celów testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Dystrybucji Zastosuj rozkład do opóźnienia** właściwości są ustawiane przy użyciu **właściwości** okna. Właściwości scenariusza testów obciążenia są modyfikowane za pomocą edytora testu obciążenia.

> [!NOTE]
> **Dystrybucji Zastosuj rozkład do opóźnienia** właściwość ma zastosowanie tylko wtedy, gdy *Załaduj test mieszany* jest skonfigurowany na podstawie tempa użytkownika. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa użytkownik wirtualny uruchomi testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Wartość **dystrybucji Zastosuj rozkład do opóźnienia** można ustawić na wartość true lub false:

- **Wartość true,**: Scenariusz ma zastosowanie normalne statystyczne rozkłady opóźnienia, które są określone przez wartość w **testy na użytkownika na godzinę** kolumny w **Edytuj Test mieszany** okno dialogowe. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa użytkownik wirtualny uruchomi testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Na przykład załóżmy, że masz **testy na użytkownika na godzinę** wartość w **Edytuj Test mieszany** okno dialogowe dla testu jest ustawiona na dwóch użytkowników na godzinę. Jeśli **dystrybucji Zastosuj rozkład do opóźnienia** właściwość jest ustawiona na **True**, normalny rozkład statystyczny jest stosowany do czasu oczekiwania między testy. Testy będą nadal działać dwóch testów na godzinę, ale nie będzie zawsze 30-minutowy opóźnienie między nimi. Pierwszy test, może uruchomić po czterech minut i drugi test po 45 minut.

- **FALSE**: Testy w tempie, który został określony dla wartości w **testy na użytkownika na godzinę** kolumny w **Edytuj Test mieszany** okno dialogowe. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa użytkownik wirtualny uruchomi testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Na przykład załóżmy, że masz **testy na użytkownika na godzinę** wartość w **Edytuj Test mieszany** okno dialogowe dla testu jest ustawiona na dwóch użytkowników na godzinę. Jeśli **dystrybucji Zastosuj rozkład do opóźnienia** właściwość jest ustawiona na **False**, spowoduje nadanie nie swobodę uruchamiania testów. Test zostanie uruchomiony co 30 minut. Dzięki temu wykonać dwa testy na godzinę.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Aby określić rozkład Zastosuj ustawienia właściwości rozkład opóźnienia dla scenariusza

1. Otwórz test obciążenia.

   **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2. W **scenariuszy** folderu drzewa testu obciążenia, wybierz opcję węzłem scenariusza, który chcesz zastosować rozkład dystrybucji.

3. Na **widoku** menu, wybierz opcję **okno właściwości**.

   Kategorie i właściwości scenariusza są wyświetlane w **właściwości** okna.

4. Wartości właściwości **dystrybucji Zastosuj rozkład do opóźnienia**, wybierz opcję **True** lub **False**.

5. Wybierz **pliku** > **Zapisz**. Teraz możesz uruchomić test obciążenia przy użyciu nowego **dystrybucji Zastosuj rozkład do opóźnienia** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)