---
title: Do testowania obciążenia, mieszanego profilu testu przeglądarki
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6694b850c7fee73e4b0891d37891e44a85f142f2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918256"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Edytuj test mieszany, aby określić, które typy przeglądarek sieci web w scenariuszu testu obciążenia

*Mieszaną przeglądarkę* umożliwia realistycznie symulować obciążenia więcej w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu różnorodnych przeglądarek sieci web zamiast jednej przeglądarki jednej sieci web. Możesz utworzyć zbliżenie przeglądarek sieci web, które będą używane z aplikacjami.

Mieszana przeglądarka określa prawdopodobieństwo, że użytkownik wirtualny uruchomi typ przeglądarki sieci web określonej w scenariuszu testu obciążenia. Podczas tworzenia testu obciążeniowego można zasymulować, czy obciążenie jest generowane przy użyciu przeglądarek sieci web. Po dodaniu typ przeglądarki sieci web do mieszanki z zestawu przeglądarki sieci web, które znajdują się zestaw skojarzone nagłówki dla wybranej przeglądarki zostanie dodany do każdego żądania HTTP, który jest przesyłany przez test wydajności sieci web.

Mieszana przeglądarka działa jak inne opcje mieszanego. Typ przeglądarki sieci web jest losowo skojarzony użytkownik wirtualny, oparte na mieszaną przeglądarkę. Tego użytkownika są testy w przeglądarce internetowej określonego, oparte na prawdopodobieństwo, że określone w zestawie.

Po określeniu mieszaną przeglądarkę można później dodać i usunąć typy przeglądarek sieci web do mieszanki. Można również zmienić rozkład przeglądarek, za pomocą formantu mieszanego. Kontrolka mieszanego pozwala łatwo dopasować rozkład przeglądarek w scenariuszu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Dodanie nowych przeglądarek do scenariusza

### <a name="to-add-new-browsers-to-a-scenario"></a>Aby dodać nowych przeglądarek do scenariusza

1. Gdy w trakcie określania wybierz przeglądarek do scenariusza **Dodaj**.

     Nowy wpis w przeglądarce jest dodawany do siatki.

    > [!NOTE]
    > Aby wyświetlić **Edytuj mieszaną przeglądarkę** okna dialogowego pole, kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz **Edytuj mieszaną przeglądarkę**.

2. W **typ przeglądarki** kolumnę, wybierz strzałkę znajdującą się nowy wpis i wybierz typ żądanego przeglądarki.

3. (Opcjonalnie) Dostosuj kontroli mieszany, aby określić rozkład testu.

4. Po zakończeniu dodawania przeglądarki, wybierz **OK**.

## <a name="remove-browsers-from-a-scenario"></a>Usuwanie przeglądarek ze scenariusza

### <a name="to-remove-browsers-from-a-scenario"></a>Aby usunąć przeglądarki ze scenariusza

1. Otwórz test obciążenia.

2. Kliknij prawym przyciskiem myszy scenariusza, z którego chcesz usunąć przeglądarkę, a następnie wybierz polecenie **Edytuj mieszaną przeglądarkę**.

     **Edytuj mieszaną przeglądarkę** zostanie wyświetlone okno dialogowe.

3. Wybierz przeglądarkę w siatce, a następnie wybierz **Usuń**.

4. (Opcjonalnie) Dostosuj kontroli mieszany, aby określić rozkład testu.

5. Po zakończeniu usuwania przeglądarki, wybierz **OK**.

## <a name="about-the-mix-control"></a>Informacje o formancie mieszany

Sterowanie mieszany umożliwia dostosowanie procent obciążenia, który jest rozproszona w ramach testów, typy przeglądarek i typy sieci w scenariuszu testu obciążenia. Wartości procentowe można dostosować, przenosząc suwaki. Dostosowywanie mieszany profil dla typów przeglądarek określa prawdopodobieństwo, że użytkownik wirtualny uruchomi typ przeglądarki w scenariuszu testu obciążenia.

Podczas przesuwania suwaka, zmień wartości procentowe wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, kwota, dodawanie lub usuwanie jest rozłożona równomiernie innych elementów. Istnieje możliwość zastąpienia tego zachowania. Jeśli zaznaczysz pole wyboru w kolumnie blokady dla określonego elementu, można zablokować określoną wartość procentową wartość dla tego elementu. Następnie podczas przesuwania suwaka, kwota, dodawanie lub usuwanie są stosowane tylko do wszystkie pozostałe elementy odblokowane.

**Dystrybucji** przycisk służy do przydzielania wartości procentowe równomiernie wszystkie elementy. Na przykład, jeśli masz trzy elementy, wybierając **dystrybucji** ustawia wartości procentowe 34, 33 i 33.

> [!WARNING]
> **Dystrybucji** przycisk zastępuje wszystkie elementy, które są zablokowane.

Istnieje również możliwość na typ wartości procentowe bezpośrednio do **%** kolumny, a nie za pomocą suwaków. Jeśli bezpośrednio wprowadzasz wartość procentową, inne elementy nie skoryguje automatycznie.

> [!NOTE]
> Suwaki są wyłączone, gdy łączny nie powoduje dodania do 100% lub wartości procentowe są wprowadzane do **%** kolumny są liczbę miejsc dziesiętnych.

Po wprowadzeniu wartości procentowe ręcznie, należy pamiętać, że sumę wszystkich elementów wynosi 100%. Podczas zapisywania mieszany, jeśli suma nie jest w 100%, możesz zostanie wyświetlony monit o zaakceptowanie wartości procentowe są one, lub przejdź wstecz i zmieniaj je tak. Jeśli zdecydujesz się je zaakceptować, ponieważ są one, będzie naliczana proporcjonalnie do 100%.  Na przykład jeśli masz dwa elementy, a następnie ręcznie ustawić je do 80% i 40%, pierwszy element zostanie ustawione na % 66,67 (80 podzielona przez 120), a drugi element zostanie ustawione na % 33,33 (40 podzielona przez 120).

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)