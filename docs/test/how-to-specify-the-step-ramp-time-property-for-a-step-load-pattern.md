---
title: Czas do zwiększenia kroku dla krokowego wzorca obciążenia dla testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f3353b6c46520dde1134c7ccff835b215b2d0ef8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107578"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Instrukcje: Określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości scenariuszy do spełnienia potrzeb i celów testowania. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

**Czas do zwiększenia kroku** właściwość jest ustawiona **właściwości** okna. Edytuj właściwości scenariusza testów obciążenia w **edytora testu obciążenia**.

**Czas do zwiększenia kroku** właściwość jest używana tylko z krokowego wzorca obciążenia. Aby uzyskać więcej informacji, zobacz [obciążenia Edytowanie wzorców do działań wirtualnego użytkownika w modelu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Krokowego wzorca obciążenia umożliwia zwiększenie obciążenia na serwerze lub serwerach, przebiegów testów obciążenia, dzięki czemu można zobaczyć, jak wydajność zmienia się wraz ze wzrostem obciążenia użytkownika. Na przykład aby zobaczyć, jak wykonać serwer lub serwery jako obciążenie użytkownikami, zwiększając do 2000 użytkowników, może uruchomić 10-godzinny test obciążenia przy użyciu krokowego wzorca obciążenia o następujących właściwościach:

- Początkowa liczba użytkowników: 100

- Maksymalna liczba użytkowników: 2000

- Czas trwania kroku (w sekundach): 1800

- Czas do zwiększenia kroku (w sekundach): 20

- Liczba użytkowników zwiększana podczas kroku: 100

Te ustawienia mają testu obciążeniowego na 30 minut (1800 sekund) uruchomiany 100, 200, 300, do 2000 użytkowników.

> [!NOTE]
> **Czas do zwiększenia kroku** właściwość jest tylko jeden z tych właściwości, która nie jest dostępna do wyboru w **nowego kreatora testu obciążenia**.

**Czas do zwiększenia kroku** właściwość umożliwia zwiększenie od jednego kroku do następnego (na przykład od 100 do 200 użytkowników) można stopniowo, a nie bezpośrednim. W przykładzie obciążenia użytkownikami zwiększyłoby się ze 100 do 200 użytkowników w okresie 20 sekund (wzrost o 5 użytkowników co sekundę).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Aby edytować właściwości czasu narastania kroku dla wzorca obciążenia krokowego

1. Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2. Obciążenia test drzew **scenariuszy** folder, otwórz węzłem scenariusza, aby określić narastania kroku czasu.

3. Wybierz **krokowego wzorca obciążenia** węzła.

    > [!NOTE]
    > Wzorzec obciążenia dla scenariusza muszą być krokowego wzorca obciążenia. Jeśli nie jest dostępne, wzorzec obciążenia będą wyświetlane typ wzorca obciążenia, który jest aktualnie powiązany z tego scenariusza. Aby uzyskać więcej informacji, zobacz [obciążenia Edytowanie wzorców do działań wirtualnego użytkownika w modelu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w **właściwości** okna.

5. Ustaw wartość **czas do zwiększenia kroku** właściwość wprowadzić liczbę dla sekund wykonane w każdym kroku, aby stopniowo dodawania użytkowników określonych przez **liczba użytkowników zwiększana podczas kroku** właściwości.

6. Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu. Następnie możesz uruchomić test obciążenia za pomocą nowego **czas do zwiększenia kroku** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie wzorców obciążenia w celu modelu aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)