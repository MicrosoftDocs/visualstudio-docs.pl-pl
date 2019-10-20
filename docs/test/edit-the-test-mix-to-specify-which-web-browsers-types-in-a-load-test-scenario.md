---
title: Test mieszany dla testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3f80da91181e4cb555d0ce96a5b4d2fb797eb0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664988"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Edytuj mieszany test, aby określić, które typy przeglądarek sieci Web w scenariuszu testu obciążenia

*Mieszanie przeglądarki* umożliwia symulowanie obciążenia w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu heterogenicznej mieszanki przeglądarek sieci Web zamiast jednej pojedynczej przeglądarki sieci Web. Tworzysz bliższe przybliżenie przeglądarek sieci Web, które będą używane z aplikacjami.

Mieszanie przeglądarki określa prawdopodobieństwo, że użytkownik wirtualny uruchamiający konkretny typ przeglądarki sieci Web w scenariuszu testu obciążenia. Podczas tworzenia testu obciążenia warto zasymulować, że obciążenie jest generowane przez więcej niż jedną przeglądarkę sieci Web. Po dodaniu typu przeglądarki sieci Web do kombinacji z dostarczonej przez siebie zestawu przeglądarek sieci Web zestaw skojarzonych nagłówków wybranej przeglądarki sieci Web jest dodawany do każdego żądania HTTP przesyłanego przez test wydajności sieci Web.

Mieszanie przeglądarki działa jak inne opcje mieszane. Typ przeglądarki sieci Web jest losowo kojarzony z użytkownikiem wirtualnym w oparciu o mieszanie przeglądarki. Testy tego użytkownika są uruchamiane w określonej przeglądarce sieci Web na podstawie prawdopodobieństwa określonego w kombinacji.

Po wybraniu przeglądarki mieszanej można później dodawać i usuwać typy przeglądarek sieci Web. Możesz również zmienić rozkład mieszany przeglądarki, używając kontrolki mix. Formant mieszany umożliwia łatwe dostosowanie dystrybucji przeglądarek w scenariuszu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Dodawanie nowych przeglądarek do scenariusza

### <a name="to-add-new-browsers-to-a-scenario"></a>Aby dodać nowe przeglądarki do scenariusza

1. W trakcie określania mieszanki przeglądarki dla scenariusza wybierz pozycję **Dodaj**.

     Do siatki zostanie dodany nowy wpis przeglądarki.

    > [!NOTE]
    > Aby wyświetlić okno dialogowe **Edytuj miks przeglądarki** , kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz polecenie **Edytuj mieszany przeglądarki**.

2. W kolumnie **Typ przeglądarki** wybierz strzałkę dla nowego wpisu i wybierz żądany typ przeglądarki.

3. Obowiązkowe Dostosuj kontrolkę mieszanie, aby określić dystrybucję testu.

4. Po zakończeniu dodawania przeglądarek wybierz **przycisk OK**.

## <a name="remove-browsers-from-a-scenario"></a>Usuwanie przeglądarek z scenariusza

### <a name="to-remove-browsers-from-a-scenario"></a>Aby usunąć przeglądarki z scenariusza

1. Otwórz test obciążenia.

2. Kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć przeglądarkę, a następnie wybierz polecenie **Edytuj mieszanie przeglądarki**.

     Zostanie wyświetlone okno dialogowe **Edytuj miks przeglądarki** .

3. Wybierz przeglądarkę w siatce, a następnie wybierz **Usuń**.

4. Obowiązkowe Dostosuj kontrolkę mieszanie, aby określić dystrybucję testu.

5. Po zakończeniu usuwania przeglądarek wybierz **przycisk OK**.

## <a name="about-the-mix-control"></a>Informacje o kontrolce mieszanej

Formant mieszany umożliwia dostosowanie wartości procentowej obciążenia, które jest dystrybuowane między testami, typami przeglądarek lub typami sieci w scenariuszu testu obciążenia. Wartości procentowe można dostosować przez przeniesienie suwaków. Dostosowanie mieszanki dla typów przeglądarek określa prawdopodobieństwo, że użytkownik wirtualny uruchamiający konkretny typ przeglądarki w scenariuszu testu obciążenia.

Przesunięcie suwaka powoduje zmianę wartości procentowej wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, ilość dodawana lub usunięta jest dystrybuowana równomiernie między innymi elementami. Istnieje możliwość zastąpienia tego zachowania. W przypadku zaznaczenia pola wyboru w kolumnie blokada dla określonego elementu należy zablokować określoną wartość procentową tego elementu. Następnie po przesunięciu suwaka ilość dodawana lub usuwana jest stosowana tylko do wszystkich pozostałych odblokowanych elementów.

Przycisk **Dystrybuuj** służy do przydzielania wartości procentowych równomiernie między wszystkimi elementami. Na przykład jeśli masz trzy elementy, wybranie opcji **Dystrybuuj** ustawia wartości procentowe na 34, 33 i 33.

> [!WARNING]
> Przycisk **Dystrybuuj** zastępuje wszystkie elementy, które są zablokowane.

Można również wpisać wartości procentowe bezpośrednio w kolumnie **%** , zamiast używać suwaków. Jeśli wprowadzisz wartość procentową bezpośrednio, pozostałe elementy nie zostaną dostosowane automatycznie.

> [!NOTE]
> Suwaki są wyłączone, gdy suma nie dodaje do 100%, lub gdy wartości procentowe wprowadzone do kolumny **%** są miejscami dziesiętnymi.

Po ręcznym wprowadzeniu wartości procentowych należy upewnić się, że suma wszystkich elementów wynosi 100%. W przypadku zapisania mieszanki, jeśli suma nie jest równa 100%, zostanie wyświetlony monit o zaakceptowanie wartości procentowych w miarę ich lub przywrócenia i dostosowania. Jeśli zdecydujesz się na ich zaakceptowanie, zostanie nadana proporcjonalnie do 100%.  Na przykład jeśli masz dwa elementy i ręcznie ustawisz je na 80% i 40%, pierwszy element zostanie ustawiony na 66,67% (80 podzielony przez 120), a drugi element zostanie ustawiony na 33,33% (40 podzielony przez 120).

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)