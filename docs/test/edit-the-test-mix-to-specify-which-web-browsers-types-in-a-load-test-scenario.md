---
title: Mieszanka testów przeglądarki do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 394331ae06760e0547cfc2b5a37a6dcd357e3614
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114535"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Edytowanie kombinacji testów w celu określenia typów przeglądarek internetowych w scenariuszu testu obciążenia

*Mix przeglądarki* umożliwia bardziej realistyczne symulowanie obciążenia w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu niejednorodnej kombinacji przeglądarek internetowych zamiast jednej przeglądarki internetowej. Tworzenie bliższe przybliżenie przeglądarek internetowych, które będą używane z aplikacjami.

Mix przeglądarki określa prawdopodobieństwo użytkownika wirtualnego z systemem określonego typu przeglądarki sieci web w scenariuszu testu obciążenia. Podczas tworzenia testu obciążenia można symulować, że obciążenie jest generowane za pośrednictwem więcej niż jednej przeglądarki sieci Web. Po dodaniu typu przeglądarki sieci Web do mieszanki z zestawu przeglądarek internetowych, które są dostarczane, zestaw skojarzonych nagłówków dla wybranej przeglądarki sieci web jest dodawany do każdego żądania HTTP, który jest przesyłany przez test wydajności sieci Web.

Mix przeglądarki działa jak inne opcje mix. Typ przeglądarki internetowej jest losowo skojarzony z użytkownikiem wirtualnym, na podstawie kombinacji przeglądarki. Testy tego użytkownika są uruchamiane w określonej przeglądarce sieci web, na podstawie prawdopodobieństwa, które zostały określone w mieszance.

Po określeniu kombinacji przeglądarki można później dodać i usunąć typy przeglądarek internetowych do miksu. Można również zmienić dystrybucję miksu przeglądarki za pomocą formantu mix. Formant miksu umożliwia łatwe dostosowanie dystrybucji przeglądarek w scenariuszu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Dodawanie nowych przeglądarek do scenariusza

### <a name="to-add-new-browsers-to-a-scenario"></a>Aby dodać nowe przeglądarki do scenariusza

1. Podczas gdy w trakcie określania kombinacji przeglądarki dla scenariusza **wybierz**dodaj .

     Nowy wpis przeglądarki zostanie dodany do siatki.

    > [!NOTE]
    > Aby wyświetlić okno dialogowe **Edytowanie miksu przeglądarki,** kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz polecenie **Edytuj miks przeglądarki**.

2. W kolumnie **Typ przeglądarki** wybierz strzałkę dla nowego wpisu i wybierz żądany typ przeglądarki.

3. (Opcjonalnie) Wyreguluj formant miksu, aby określić rozkład testowy.

4. Po zakończeniu dodawania przeglądarek wybierz przycisk **OK**.

## <a name="remove-browsers-from-a-scenario"></a>Usuwanie przeglądarek ze scenariusza

### <a name="to-remove-browsers-from-a-scenario"></a>Aby usunąć przeglądarki ze scenariusza

1. Otwórz test obciążenia.

2. Kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć przeglądarkę, a następnie wybierz polecenie **Edytuj miks przeglądarki**.

     Zostanie wyświetlone okno dialogowe **Edytowanie miksu przeglądarki.**

3. Wybierz przeglądarkę w siatce, a następnie wybierz pozycję **Usuń**.

4. (Opcjonalnie) Wyreguluj formant miksu, aby określić rozkład testowy.

5. Po zakończeniu usuwania przeglądarek wybierz przycisk **OK**.

## <a name="about-the-mix-control"></a>Informacje o kontroli mieszania

Formant mieszania umożliwia dostosowanie procent obciążenia, który jest rozdzielany między testy, typy przeglądarki lub typy sieci w scenariuszu testu obciążenia. Wartości procentowe można dostosować, przesuwając suwaki. Dostosowanie kombinacji dla typów przeglądarki określa prawdopodobieństwo, że użytkownik wirtualny uruchamia określony typ przeglądarki w scenariuszu testu obciążenia.

Podczas przenoszenia suwaka zmieniają się wartości procentowe wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, kwota dodana lub wyrównana jest rozłożona równomiernie między inne elementy. Istnieje możliwość zastąpienia tego zachowania. Jeśli zaznaczysz pole wyboru w kolumnie blokady dla określonego elementu, zostanie zablokowana określona wartość procentowa dla tego elementu. Następnie po przeniesieniu suwaka kwota dodania lub usunięcia jest stosowana tylko do pozostałych odblokowanych elementów.

**Przycisk Rozłóż** służy do równego przydzielania wartości procentowych między wszystkie elementy. Na przykład jeśli masz trzy elementy, wybranie opcji **Rozmieść** ustawia wartości procentowe na 34, 33 i 33.

> [!WARNING]
> Przycisk **Rozłóż** zastępuje wszystkie elementy, które są zablokowane.

Możliwe jest również wpisanie wartości procentowych **%** bezpośrednio w kolumnie zamiast za pomocą suwaków. Jeśli wprowadzisz wartość procentową bezpośrednio, pozostałe elementy nie zostaną automatycznie dostosowane.

> [!NOTE]
> Suwaki są wyłączone, gdy suma nie sumuje się do 100%, **%** lub gdy wartości procentowe wprowadzone w kolumnie są dziesiętne.

Podczas ręcznego wprowadzania wartości procentowych należy upewnić się, że suma wszystkich elementów wynosi 100%. Po zapisaniu mieszanki, jeśli suma nie jest 100%, zostanie wyświetlony monit o zaakceptowanie wartości procentowych w ich stanie lub o ich powrót i dostosowanie. Jeśli zdecydujesz się je zaakceptować w taki sposób, w jaki są, będą one proporcjonalnie do 100%.  Na przykład, jeśli masz dwa elementy i ręcznie ustawisz je na 80% i 40%, pierwszy element zostanie ustawiony na 66,67% (80 podzielonych przez 120), a drugi element zostanie ustawiony na 33,33% (40 podzielonych przez 120).

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
