---
title: Mieszanka testowa dla scenariusza testu obciążenia
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595933"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Edytuj kombinację testów, aby określić, które testy wydajności sieci web, jednostki i kodowane interfejsu użytkownika mają być uwzględnione w scenariuszu testu obciążenia

*Test mix* scenariusza jest kombinacją wyboru wydajności sieci web i testów jednostkowych, które są zawarte w scenariuszu i dystrybucji tych testów w scenariuszu. Rozkład jest ustawieniem, które można określić dla prawdopodobieństwa, że określony test zostanie wybrany przez użytkownika wirtualnego podczas przebiegu testu obciążenia.

Po dodaniu zestawu testów do testu *obciążenia, test mix* działa podobnie jak inne opcje mieszania. Użytkownik wirtualny losowo wybiera test, na podstawie prawdopodobieństwa, które zostały określone w mieszance. Na przykład jeśli masz dwa testy, każdy 50 procent w mieszance, nowy użytkownik wirtualny zdecyduje się uruchomić pierwszy test około połowy czasu. W mieszance 50/50, jeśli jeden test jest długi, a drugi jest krótki, większe obciążenie pochodzi z długiego testu.

Po dodaniu testów do mieszanki można je usunąć. Można również zmienić rozkład testu mix za pomocą kontroli mix. Formant miksu umożliwia łatwe dostosowanie rozkładu testów w scenariuszu.

> [!NOTE]
> Dystrybucja jest miarą prawdopodobieństwa, że określony test zostanie wybrany przez użytkownika wirtualnego podczas przebiegu testu obciążenia. Rozkład jest wyrażony jako procent. W związku z tym suma numerów dystrybucyjnych dla wszystkich testów, które są zawarte w scenariuszu jest 100. Na przykład jeśli scenariusz zawiera tylko jeden test, dystrybucja dla tego testu jest 100 procent.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Dodawanie nowych testów do kombinacji testowej w istniejącym scenariuszu

Podczas tworzenia nowego scenariusza przy użyciu **Kreatora nowego testu obciążenia**można określić wydajność sieci web i testy jednostkowe, aby dodać do zestawu testów nowego scenariusza.

Można dodać więcej testów wydajności sieci web i jednostek do kombinacji tekstu scenariusza za pomocą **Edytora testów obciążenia**.

![Dodawanie testu do istniejącego testu obciążenia](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Aby dodać więcej testów do istniejącego scenariusza

1. Otwórz test obciążenia.

2. W **Edytorze testów obciążenia**kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz polecenie **Dodaj testy**.

     Zostanie wyświetlone okno dialogowe **Dodawanie testów.** Wszystkie testy wydajności sieci web, jednostki i kodowane interfejsu użytkownika w rozwiązaniu, które nie są jeszcze w scenariuszu są dostępne do dodania do scenariusza.

3. W okienku **Dostępne testy** wybierz testy wydajności sieci web, jednostki i kodowane interfejsu użytkownika, które chcesz dodać. Wybierz strzałkę w prawo, aby dodać testy do okienka **Wybrane testy.**

4. Po zakończeniu dodawania testów wybierz przycisk **OK**.

     Testy są dodawane do mieszanki testowej. Nowa dystrybucja jest automatycznie przypisywana do testów w zestawieniu testowym.

5. (Opcjonalnie) Wyreguluj formant miksu, aby określić rozkład testowy. Aby uzyskać więcej informacji, zobacz [Informacje o formancie mieszania](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Usuwanie testów ze scenariusza
![Usuwanie testu z istniejącego testu obciążenia](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Aby usunąć testy ze scenariusza

1. Otwórz test obciążenia.

2. W **Edytorze testów obciążenia**w drzewie testu obciążenia kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć test, i wybierz polecenie **Edytuj miks testowy**. Zostanie wyświetlone okno dialogowe **Edytowanie miksu testowego.**

3. Wybierz test wydajności sieci Web, jednostki lub zakodowany interfejs użytkownika w siatce, a następnie wybierz pozycję **Usuń**.

    > [!NOTE]
    > Po usunięciu testu dostosuj miks testowy do preferowanego rozkładu.

4. Po zakończeniu usuwania testów wybierz przycisk **OK**.

## <a name="about-the-mix-control"></a><a name="EditingTestMixAboutMixControl"></a>Informacje o kontroli miksu
Formant mieszania umożliwia dostosowanie procent obciążenia, który jest rozdzielany między testy, typy przeglądarki lub typy sieci w scenariuszu testu obciążenia. Wartości procentowe można dostosować, przesuwając suwaki. Dostosowanie kombinacji do testów określa prawdopodobieństwo, że użytkownik wirtualny uruchomi określony test w scenariuszu testu obciążenia.

Podczas przenoszenia suwaka zmieniają się wartości procentowe wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, kwota dodana lub wyrównana jest rozłożona równomiernie między inne elementy. Istnieje możliwość zastąpienia tego zachowania. Jeśli zaznaczysz pole wyboru w kolumnie blokady dla określonego elementu, zostanie zablokowana określona wartość procentowa dla tego elementu. Następnie po przeniesieniu suwaka kwota dodania lub usunięcia jest stosowana tylko do pozostałych odblokowanych elementów.

**Przycisk Rozłóż** służy do równego przydzielania wartości procentowych między wszystkimi elementami. Na przykład jeśli masz trzy elementy, wybranie opcji **Rozmieść** ustawia wartości procentowe na 34, 33 i 33.

> [!WARNING]
> Przycisk **Rozłóż** zastępuje wszystkie elementy, które są zablokowane.

Możliwe jest również wpisanie wartości procentowych **%** bezpośrednio w kolumnie zamiast za pomocą suwaków. Jeśli wprowadzisz wartość procentową bezpośrednio, pozostałe elementy nie zostaną automatycznie dostosowane.

> [!NOTE]
> Suwaki są wyłączone, gdy suma nie sumuje się do 100%, **%** lub gdy wartości procentowe wprowadzone w kolumnie są dziesiętne.

Podczas ręcznego wprowadzania wartości procentowych należy upewnić się, że suma wszystkich elementów wynosi 100%. Po zapisaniu mieszanki, jeśli suma nie jest 100%, zostanie wyświetlony monit o zaakceptowanie wartości procentowych w ich stanie lub o ich powrót i dostosowanie. Jeśli zdecydujesz się je zaakceptować w taki sposób, w jaki są, będą one proporcjonalnie do 100%.  Na przykład, jeśli masz dwa elementy i ręcznie ustawisz je na 80% i 40%, pierwszy element zostanie ustawiony na 66,67% (80 podzielonych przez 120), a drugi element zostanie ustawiony na 33,33% (40 podzielonych przez 120).

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
