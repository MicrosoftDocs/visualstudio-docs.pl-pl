---
title: Czas zwiększania kroku wzorca obciążenia dla testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a40f7ce4aacfdc03b5e05becbfc83439945f7e8a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588918"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Instrukcje: Określanie właściwości czasu rampy kroku dla wzorca obciążenia krok po kroku

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości scenariuszy do spełnienia potrzeb i celów testowania. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

Właściwość **czas rampy kroku** jest ustawiana w oknie **Właściwości** . Edytuj właściwości scenariusza testów obciążenia w **edytora testu obciążenia**.

Właściwość **czas pochylni kroku** jest używana tylko z wzorcem ładowania kroku. Aby uzyskać więcej informacji, zobacz [obciążenia Edytowanie wzorców do działań wirtualnego użytkownika w modelu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Wzorzec obciążenia kroków służy do zwiększania obciążenia serwera lub serwerów w miarę przebiegu testu obciążenia, dzięki czemu można zobaczyć, jak wydajność zmienia się w miarę wzrostu obciążenia użytkownika. Na przykład, aby zobaczyć, jak serwer lub serwery działają w miarę wzrostu obciążenia użytkownika 2 000 użytkowników, można uruchomić 10-godzinny test obciążenia, korzystając ze wzorca ładowania kroków o następujących właściwościach:

- Początkowa liczba użytkowników: 100

- Maksymalna liczba użytkowników: 2000

- Czas trwania kroku (w sekundach): 1800

- Czas pochylenia kroku (w sekundach): 20

- Liczba użytkowników kroku: 100

Te ustawienia mają uruchomiony test obciążenia przez 30 minut (1800 sekund) na obciążeniach użytkowników 100, 200, 300, aż do 2 000 użytkowników.

> [!NOTE]
> Właściwość **czas rampy kroku** jest jedyną jedną z tych właściwości, które nie są dostępne do wyboru w **nowym Kreator testu obciążeniowego**.

Właściwość **czas rampy kroku** pozwala zwiększyć się od jednego kroku do następnego (na przykład od 100 do 200 użytkowników), a nie bezpośrednio. W tym przykładzie obciążenie użytkownikami zostanie zwiększone od 100 do 200 użytkowników w ciągu 20 sekund (w każdej sekundzie wynosi 5 użytkowników).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Aby edytować Właściwość czas rampy kroku dla wzorca obciążenia krok po kroku

1. Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **scenariusze** dla drzew testów obciążenia Otwórz węzeł scenariusza, dla którego chcesz określić czas przyrastania kroku.

3. Wybierz węzeł **wzorzec obciążenia krok po kroku** .

    > [!NOTE]
    > Wzorzec obciążenia dla scenariusza musi być wzorcem obciążenia etapem. Jeśli tak nie jest, wzorzec obciążenia będzie wyświetlał typ wzorca obciążenia, który jest aktualnie skojarzony z scenariuszem. Aby uzyskać więcej informacji, zobacz [obciążenia Edytowanie wzorców do działań wirtualnego użytkownika w modelu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w **właściwości** okna.

5. Ustaw wartość właściwości czas narastania **kroku** , wprowadzając liczbę dla sekund podejmowanych w każdym kroku w celu stopniowego dodawania użytkowników określonych przez właściwość **Liczba użytkowników kroków** .

6. Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu. Następnie możesz uruchomić test obciążenia, korzystając z nowej wartości **czasu pochylenia kroku** .

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie wzorców obciążenia w celu modelu aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)
