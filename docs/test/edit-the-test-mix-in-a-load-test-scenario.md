---
title: Test mieszany w scenariuszu testu obciążenia
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
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 8a54c20d90edacbd29169320bc746e5b9cb724f9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905322"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Edytuj test mieszany, aby określić, które wydajności sieci web, jednostki i kodowane testy interfejsu użytkownika można uwzględnić w scenariuszu testu obciążenia

*Test mieszany* scenariusz składa się z wybranych sieci web wydajności i testy jednostkowe, które są zawarte w tym scenariuszu i dystrybucji tych testów, w tym scenariuszu. Dystrybucja to ustawienie można określić prawdopodobieństwo, że konkretnego testu zostanie wybrany przez użytkownika wirtualnego podczas przebiegu testu obciążenia.

Po dodaniu zestawu testów do testu obciążeniowego *test mieszany* podobnie jak inne mieszać opcji. Użytkownik wirtualny losowo wybiera test, oparty na prawdopodobieństwo, że określone w zestawie. Na przykład w przypadku dwóch testów, każdy 50 procent w asortymencie, nowego użytkownika wirtualnego decyduje się pierwszy test około połowę czasu uruchomienia. W asortymencie 50/50 Jeśli jeden test jest długa i inny jest krótki, większe obciążenie jest dostarczany z długiego testu.

Po dodaniu testy do mieszanki można je usunąć. Można również zmienić dystrybucji testu mieszanego, za pomocą formantu mieszanego. Formant mieszanego pozwala łatwo dopasować rozkład testów w scenariuszu.

> [!NOTE]
> Dystrybucja jest miarą prawdopodobieństwo, że konkretnego testu zostanie wybrany przez użytkownika wirtualnego podczas przebiegu testu obciążenia. Dystrybucja jest wyrażona w procentach. W związku z tym sumę liczb dystrybucji dla wszystkich testów, które są zawarte w scenariuszu to 100. Na przykład jeśli scenariusz zawiera tylko jeden test, dystrybucji dla tego testu jest 100 procent.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Dodaj nowe testy do mieszanki testów, w istniejącego scenariusza

Gdy tworzysz nowy scenariusz przy użyciu **Kreatora nowego testu obciążenia**, można określić testy wydajności i jednostki sieci web, aby dodać do testu mieszanego nowy scenariusz.

Można dodać więcej web wydajności i testy jednostkowe do mieszanki tekstu scenariusza za pomocą **edytora testu obciążenia**.

![Dodawanie testu do istniejącego testu obciążenia](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Aby dodać więcej testów do istniejącego scenariusza

1.  Otwórz test obciążenia.

2.  W **edytora testu obciążenia**, kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz **Dodaj testy**.

     **Dodaj testy** zostanie wyświetlone okno dialogowe. Wydajności sieci web, jednostki i kodowane testy interfejsu użytkownika w rozwiązaniu, które nie są już w tym scenariuszu są dostępne dodać do scenariusza.

3.  W **dostępne testy** okienku zaznacz wydajności sieci web, jednostki i kodowane testy interfejsu użytkownika, które chcesz dodać. Wybierz strzałkę w prawo, aby dodać testy **wybrane testy** okienka.

4.  Po dodaniu testów wybierz **OK**.

     Testy zostaną dodane do testu mieszanego. Nowe dystrybucji jest automatycznie przypisywany do testy w asortymencie test.

5.  (Opcjonalnie) Dostosuj kontroli mieszany, aby określić rozkład testu. Aby uzyskać więcej informacji, zobacz [informacje o formancie mieszanego](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

##  <a name="remove-tests-from-a-scenario"></a>Usuń testy ze scenariusza
 ![Usuwanie testu z istniejącego testu obciążenia](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Aby usunąć testy ze scenariusza

1.  Otwórz test obciążenia.

2.  W **edytora testu obciążenia**, obciążenia test drzewa, kliknij prawym przyciskiem myszy scenariusza, z którego chcesz usunąć test i wybierz pozycję **Edytuj Test mieszany**. **Edytuj Test mieszany** zostanie wyświetlone okno dialogowe.

3.  Wybierz wydajność sieci web, jednostki lub kodowany test interfejsu użytkownika w siatce, a następnie wybierz **Usuń**.

    > [!NOTE]
    > Po usunięciu testu dopasować test mieszany do Twojej dystrybucji.

4.  Aby zakończyć usuwanie testów, wybierz **OK**.

##  <a name="EditingTestMixAboutMixControl"></a> Informacje o formancie mieszany
 Sterowanie mieszany umożliwia dostosowanie procent obciążenia, który jest rozproszona w ramach testów, typy przeglądarek i typy sieci w scenariuszu testu obciążenia. Wartości procentowe można dostosować, przenosząc suwaki. Dostosowywanie mieszanki testów określa prawdopodobieństwo, że użytkownik wirtualny uruchomi określony test w scenariuszu testu obciążenia.

 Podczas przesuwania suwaka, zmień wartości procentowe wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, kwota, dodawanie lub usuwanie jest rozłożona równomiernie innych elementów. Istnieje możliwość zastąpienia tego zachowania. Jeśli zaznaczysz pole wyboru w kolumnie blokady dla określonego elementu, można zablokować określoną wartość procentową wartość dla tego elementu. Następnie podczas przesuwania suwaka, kwota, dodawanie lub usuwanie są stosowane tylko do wszystkie pozostałe elementy odblokowane.

 **Dystrybucji** przycisk służy do przydzielania wartości procentowych równomiernie wszystkie elementy. Na przykład, jeśli masz trzy elementy, wybierając **dystrybucji** ustawia wartości procentowe 34, 33 i 33.

> [!WARNING]
> **Dystrybucji** przycisk zastępuje wszystkie elementy, które są zablokowane.


 Istnieje również możliwość na typ wartości procentowe bezpośrednio do **%** kolumny, a nie za pomocą suwaków. Jeśli bezpośrednio wprowadzasz wartość procentową, inne elementy nie skoryguje automatycznie.

> [!NOTE]
> Suwaki są wyłączone, gdy łączny nie powoduje dodania do 100% lub wartości procentowe są wprowadzane do **%** kolumny są liczbę miejsc dziesiętnych.


 Po wprowadzeniu wartości procentowe ręcznie, należy pamiętać, że sumę wszystkich elementów wynosi 100%. Podczas zapisywania mieszany, jeśli suma nie jest w 100%, możesz zostanie wyświetlony monit o zaakceptowanie wartości procentowe są one, lub przejdź wstecz i zmieniaj je tak. Jeśli zdecydujesz się je zaakceptować, ponieważ są one, będzie naliczana proporcjonalnie do 100%.  Na przykład jeśli masz dwa elementy, a następnie ręcznie ustawić je do 80% i 40%, pierwszy element zostanie ustawione na % 66,67 (80 podzielona przez 120), a drugi element zostanie ustawione na % 33,33 (40 podzielona przez 120).

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)