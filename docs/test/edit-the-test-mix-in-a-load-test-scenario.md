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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f28a9be17bba0bf7fc8fa4ea2198a255a2cbde53
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918305"
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

5. (Opcjonalnie) Dostosuj kontroli mieszany, aby określić rozkład testu. Aby uzyskać więcej informacji, zobacz [informacje o formancie mieszanego](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Usuwanie testów z scenariusza
![Usuwanie testu z istniejącego testu obciążenia](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Aby usunąć testy z scenariusza

1. Otwórz test obciążenia.

2. W **Edytor testu obciążeniowego**w drzewie testu obciążenia kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć test, a następnie wybierz pozycję **Edytuj test mieszany**. **Edytuj Test mieszany** zostanie wyświetlone okno dialogowe.

3. Wybierz test wydajność sieci Web, jednostkę lub kodowany interfejs użytkownika w siatce, a następnie wybierz **Usuń**.

    > [!NOTE]
    > Po usunięciu testu Dostosuj test mieszany do preferowanej dystrybucji.

4. Po zakończeniu usuwania testów wybierz **przycisk OK**.

## <a name="EditingTestMixAboutMixControl"></a>Informacje o kontrolce mieszanej
Sterowanie mieszany umożliwia dostosowanie procent obciążenia, który jest rozproszona w ramach testów, typy przeglądarek i typy sieci w scenariuszu testu obciążenia. Wartości procentowe można dostosować, przenosząc suwaki. Dostosowanie mieszanki dla testów określa prawdopodobieństwo, że użytkownik wirtualny uruchamia konkretny test w scenariuszu testu obciążenia.

Podczas przesuwania suwaka, zmień wartości procentowe wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, kwota, dodawanie lub usuwanie jest rozłożona równomiernie innych elementów. Istnieje możliwość zastąpienia tego zachowania. Jeśli zaznaczysz pole wyboru w kolumnie blokady dla określonego elementu, można zablokować określoną wartość procentową wartość dla tego elementu. Następnie podczas przesuwania suwaka, kwota, dodawanie lub usuwanie są stosowane tylko do wszystkie pozostałe elementy odblokowane.

Przycisk **Dystrybuuj** służy do przydzielania wartości procentowych równomiernie między wszystkimi elementami. Na przykład, jeśli masz trzy elementy, wybierając **dystrybucji** ustawia wartości procentowe 34, 33 i 33.

> [!WARNING]
> **Dystrybucji** przycisk zastępuje wszystkie elementy, które są zablokowane.

Istnieje również możliwość na typ wartości procentowe bezpośrednio do **%** kolumny, a nie za pomocą suwaków. Jeśli bezpośrednio wprowadzasz wartość procentową, inne elementy nie skoryguje automatycznie.

> [!NOTE]
> Suwaki są wyłączone, gdy łączny nie powoduje dodania do 100% lub wartości procentowe są wprowadzane do **%** kolumny są liczbę miejsc dziesiętnych.

Po wprowadzeniu wartości procentowe ręcznie, należy pamiętać, że sumę wszystkich elementów wynosi 100%. Podczas zapisywania mieszany, jeśli suma nie jest w 100%, możesz zostanie wyświetlony monit o zaakceptowanie wartości procentowe są one, lub przejdź wstecz i zmieniaj je tak. Jeśli zdecydujesz się je zaakceptować, ponieważ są one, będzie naliczana proporcjonalnie do 100%.  Na przykład jeśli masz dwa elementy, a następnie ręcznie ustawić je do 80% i 40%, pierwszy element zostanie ustawione na % 66,67 (80 podzielona przez 120), a drugi element zostanie ustawione na % 33,33 (40 podzielona przez 120).

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)