---
title: Krok Ramp Time dla wzorca obciążenia kroku do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a40f7ce4aacfdc03b5e05becbfc83439945f7e8a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588918"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Jak: Określ właściwość czasu rampy kroku dla wzorca obciążenia kroku

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić właściwości scenariuszy, aby spełnić twoje potrzeby i cele testowania. Aby uzyskać więcej informacji, zobacz [Instruktaż: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisy, zobacz [Właściwości scenariusza testu obciążenia.](../test/load-test-scenario-properties.md)

Właściwość **Krok Czas rampy** jest ustawiona w oknie **Właściwości.** Można edytować właściwości scenariusza testu obciążenia w **Edytorze testów obciążenia**.

Właściwość **Krok Ramp Time** jest używany tylko ze wzorcem obciążenia kroku. Aby uzyskać więcej informacji, zobacz [Edytowanie wzorców obciążenia w celu modelowania działań użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Wzorzec obciążenia krok jest używany do zwiększenia obciążenia na serwerze lub serwerach w miarę wykonywania testu obciążenia, dzięki czemu można zobaczyć, jak wydajność zmienia się wraz ze wzrostem obciążenia użytkownika. Na przykład, aby zobaczyć, jak serwer lub serwery działają w miarę zwiększania obciążenia użytkownika do 2000 użytkowników, można uruchomić 10-godzinny test obciążenia przy użyciu wzorca obciążenia krokowego z następującymi właściwościami:

- Początkowa liczba użytkowników: 100

- Maksymalna liczba użytkowników: 2000

- Czas trwania kroku (w sekundach): 1800

- Krok Ramp Czas (sekundy): 20

- Liczba użytkowników kroków: 100

Te ustawienia mają test obciążenia uruchomiony przez 30 minut (1800 sekund) przy obciążeniach użytkownika 100, 200, 300, do 2000 użytkowników.

> [!NOTE]
> Właściwość **Krok Czas rampy** jest jedyną z tych właściwości, która nie jest dostępna do wyboru w **Kreatorze nowego testu obciążenia.**

**Właściwość Step Ramp Time** umożliwia zwiększenie z jednego kroku do następnego (na przykład od 100 do 200 użytkowników) jest stopniowe, a nie natychmiastowe. W tym przykładzie obciążenie użytkownika zostanie zwiększone ze 100 do 200 użytkowników w okresie 20 sekund (wzrost o 5 użytkowników co sekundę).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Aby edytować właściwość czasu rampy kroku dla wzorca obciążenia kroku

1. Otwórz test obciążenia.

     Pojawi się **Edytor testów obciążenia.** Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **Scenariusze** drzew testów obciążenia otwórz węzeł scenariusza, dla którego chcesz określić czas rampy kroku.

3. Wybierz węzeł **Wzorzec obciążenia kroku.**

    > [!NOTE]
    > Wzorzec obciążenia dla scenariusza musi być wzorzec obciążenia kroku. Jeśli tak nie jest, wzorzec obciążenia wyświetli typ wzorca obciążenia, który jest obecnie skojarzony ze scenariuszem. Aby uzyskać więcej informacji, zobacz [Edytowanie wzorców obciążenia w celu modelowania działań użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości.**

5. Ustaw wartość właściwości **Step Ramp Time,** wprowadzając liczbę dla sekund wykonanych w każdym kroku, aby stopniowo dodawać użytkowników określonych przez właściwość **Liczba użytkowników kroku.**

6. Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowej wartości **krok rampa czas.**

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie wzorców obciążenia w celu modelowania działań użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md)
