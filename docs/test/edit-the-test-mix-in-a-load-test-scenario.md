---
title: Test mieszany dla scenariusza testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a52d660140416ce829493a733171cfcf64ebbe4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595933"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Edytuj mieszany test, aby określić, które testy wydajności sieci Web, jednostki i kodowanego interfejsu użytkownika mają być uwzględnione w scenariuszu testu obciążenia

*Test mieszany* scenariusza jest połączeniem wyboru wydajności sieci Web i testów jednostkowych, które są zawarte w scenariuszu i rozkładu tych testów w scenariuszu. Dystrybucja jest ustawieniem, które można określić dla prawdopodobieństwa, że określony test zostanie wybrany przez użytkownika wirtualnego podczas przebiegu testu obciążenia.

Po dodaniu zestawu testów do testu obciążenia, *test mieszany* działa jak inne opcje mieszane. Użytkownik wirtualny losowo wybiera test, na podstawie prawdopodobieństwa określonego w kombinacji. Na przykład jeśli masz dwa testy, każdy 50 procent w połączeniu, nowy użytkownik wirtualny zdecyduje się na uruchomienie pierwszego testu około połowy czasu. W przypadku 50/50 mieszanej, jeśli jeden test jest długi i drugi jest krótki, większe obciążenie pochodzi z długiego testu.

Po dodaniu testów do mieszania można je usunąć. Można również zmienić rozkład testu mieszanego za pomocą kontrolki mieszanej. Formant mieszany umożliwia łatwe dostosowanie dystrybucji testów w scenariuszu.

> [!NOTE]
> Dystrybucja jest miarą prawdopodobieństwa, że konkretny test zostanie wybrany przez użytkownika wirtualnego podczas przebiegu testu obciążenia. Dystrybucja jest wyrażona jako wartość procentowa. W związku z tym Suma numerów dystrybucji dla wszystkich testów, które są zawarte w scenariuszu, wynosi 100. Na przykład jeśli scenariusz zawiera tylko jeden test, dystrybucja dla tego testu wynosi 100%.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Dodawanie nowych testów do testu mieszanego w istniejącym scenariuszu

Podczas tworzenia nowego scenariusza przy użyciu **nowego Kreator testu obciążeniowego**można określić testy wydajności sieci Web i jednostki, które mają zostać dodane do testu mieszanego w nowym scenariuszu.

Aby dowiedzieć się więcej o wydajności sieci Web i testach jednostkowych, możesz użyć **Edytor testu obciążeniowego**.

![Dodawanie testu do istniejącego testu obciążenia](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Aby dodać więcej testów do istniejącego scenariusza

1. Otwórz test obciążenia.

2. W **Edytor testu obciążeniowego**kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz polecenie **Dodaj testy**.

     Zostanie wyświetlone okno dialogowe **Dodawanie testów** . Wszystkie testy wydajności sieci Web, jednostki i kodowanego interfejsu użytkownika w rozwiązaniu, które nie znajdują się jeszcze w Twoim scenariuszu, są dostępne do dodania do tego scenariusza.

3. W okienku **dostępne testy** wybierz testy wydajności sieci Web, jednostki i KODOWANEGO interfejsu użytkownika, które chcesz dodać. Wybierz strzałkę w prawo, aby dodać testy do okienka **Wybrane testy** .

4. Po zakończeniu dodawania testów wybierz **przycisk OK**.

     Testy są dodawane do testu mieszanego. Nowa dystrybucja jest automatycznie przypisywana do testów w teście mieszanym.

5. Obowiązkowe Dostosuj kontrolkę mieszanie, aby określić dystrybucję testu. Aby uzyskać więcej informacji, zobacz [Informacje o kontrolce mieszanej](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Usuwanie testów z scenariusza
![Usuwanie testu z istniejącego testu obciążenia](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Aby usunąć testy z scenariusza

1. Otwórz test obciążenia.

2. W **Edytor testu obciążeniowego**w drzewie testu obciążenia kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć test, a następnie wybierz pozycję **Edytuj test mieszany**. Zostanie wyświetlone okno dialogowe **Edytowanie testu mieszanego** .

3. Wybierz test wydajność sieci Web, jednostkę lub kodowany interfejs użytkownika w siatce, a następnie wybierz **Usuń**.

    > [!NOTE]
    > Po usunięciu testu Dostosuj test mieszany do preferowanej dystrybucji.

4. Po zakończeniu usuwania testów wybierz **przycisk OK**.

## <a name="about-the-mix-control"></a><a name="EditingTestMixAboutMixControl"></a> Informacje o kontrolce mieszanej
Formant mieszany umożliwia dostosowanie wartości procentowej obciążenia, które jest dystrybuowane między testami, typami przeglądarek lub typami sieci w scenariuszu testu obciążenia. Wartości procentowe można dostosować przez przeniesienie suwaków. Dostosowanie mieszanki dla testów określa prawdopodobieństwo, że użytkownik wirtualny uruchamia konkretny test w scenariuszu testu obciążenia.

Przesunięcie suwaka powoduje zmianę wartości procentowej wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, ilość dodawana lub usunięta jest dystrybuowana równomiernie między innymi elementami. Istnieje możliwość zastąpienia tego zachowania. W przypadku zaznaczenia pola wyboru w kolumnie blokada dla określonego elementu należy zablokować określoną wartość procentową tego elementu. Następnie po przesunięciu suwaka ilość dodawana lub usuwana jest stosowana tylko do wszystkich pozostałych odblokowanych elementów.

Przycisk **Dystrybuuj** służy do przydzielania wartości procentowych równomiernie między wszystkimi elementami. Na przykład jeśli masz trzy elementy, wybranie opcji **Dystrybuuj** ustawia wartości procentowe na 34, 33 i 33.

> [!WARNING]
> Przycisk **Dystrybuuj** zastępuje wszystkie elementy, które są zablokowane.

Można również wpisać wartości procentowe bezpośrednio w **%** kolumnie zamiast używać suwaków. Jeśli wprowadzisz wartość procentową bezpośrednio, pozostałe elementy nie zostaną dostosowane automatycznie.

> [!NOTE]
> Suwaki są wyłączone, gdy suma nie dodaje do 100%, lub gdy wartości procentowe wprowadzone do **%** kolumny są miejscami dziesiętnymi.

Po ręcznym wprowadzeniu wartości procentowych należy upewnić się, że suma wszystkich elementów wynosi 100%. W przypadku zapisania mieszanki, jeśli suma nie jest równa 100%, zostanie wyświetlony monit o zaakceptowanie wartości procentowych w miarę ich lub przywrócenia i dostosowania. Jeśli zdecydujesz się na ich zaakceptowanie, zostanie nadana proporcjonalnie do 100%.  Na przykład jeśli masz dwa elementy i ręcznie ustawisz je na 80% i 40%, pierwszy element zostanie ustawiony na 66,67% (80 podzielony przez 120), a drugi element zostanie ustawiony na 33,33% (40 podzielony przez 120).

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
