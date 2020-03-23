---
title: Analizowanie aktywności użytkownika wirtualnego pod kątem testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c997f27e65a8e3992239fac78d52b0b4f19670c3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169407"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Jak: Analizowanie, co użytkownicy wirtualni robią podczas testu obciążenia przy użyciu wykresu aktywności użytkownika wirtualnego

Wyświetlanie aktywności użytkownika wirtualnego skojarzonego z testem obciążenia przy użyciu **wykresu aktywności użytkownika wirtualnego**. Każdy wiersz na wykresie reprezentuje indywidualnego użytkownika wirtualnego. **Wykres aktywności użytkownika wirtualnego** pokazuje dokładnie to, co każdy użytkownik wirtualny był wykonywany podczas testu. Można zobaczyć wzorce aktywności użytkownika, wzorców obciążenia, skorelować testy nie powiodło się lub powolne i wyświetlić żądania z innymi działaniami użytkownika wirtualnego. **Wykres aktywności użytkownika wirtualnego** jest dostępny tylko po zakończeniu testu obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Poniższe procedury pokazują, jak wyświetlić **wykres aktywności użytkownika wirtualnego,** jak zbadać aktywność określonego użytkownika i jak korzystać z filtrowania.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby wyświetlić wykres aktywności użytkownika wirtualnego w wynikach testu obciążenia

1. Aby wyświetlić dane użytkownika wirtualnego, należy najpierw skonfigurować ustawienie **Wszystkie szczegóły indywidualne** dla właściwości Magazyn szczegółów **chronometrażu** skojarzonej z testem obciążenia. Następnie uruchom test obciążenia.

2. Po uruchomieniu testu obciążenia zostanie wyświetlona strona podsumowania wyników testu. Wybierz przycisk **Szczegóły użytkownika** na pasku narzędzi.

     — lub —

     Otwórz widok Wykresy, wybierając przycisk **Wykresy** na pasku narzędzi. Kliknij prawym przyciskiem myszy wykres, a następnie wybierz polecenie **Przejdź do szczegółów użytkownika**.

     Jeśli użyjesz tej opcji, **wykres aktywności użytkownika wirtualnego** zostanie automatycznie powiększony do części testu, która została kliknięta prawym przyciskiem myszy. Jeśli na przykład wskaźnik znajduje się w przybliżeniu na znaku 30 sekund, widok szczegółów będzie wyświetlany w przybliżeniu na 30-sekundowym znaczniku w narzędziu **Powiększenie do okresu czasu** u dołu **wykresu aktywności użytkownika wirtualnego**.

     Następnie można użyć zbadać szczegóły aktywności określonego użytkownika w **wirtualnym wykresie aktywności użytkownika**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Aby zbadać aktywność określonego użytkownika na wykresie aktywności użytkownika wirtualnego

1. Użyj narzędzia Powiększenie do okresu czasu u dołu **wykresu aktywności użytkownika wirtualnego,** aby wybrać obszar na wykresie, w którym chcesz zbadać szczegóły dotyczące określonego użytkownika.

2. Umieść wskaźnik myszy na szczegółach na wykresie. Należy zauważyć, że w końcówce narzędzia wyświetlane są następujące informacje:

   - **Identyfikator użytkownika**

   - **Scenariusz**

   - **Test**

   - **Adres URL** (nie jest wyświetlany w teście lub transakcji)

   - **Wynik**

   - **Przeglądarka** (nie jest wyświetlana w teście lub transakcji)

   - **Sieć**

   - **Godzina rozpoczęcia**

   - **Czas trwania**

   - **Agent**

   - **Dziennik testów** (łącze do dziennika testów)

     > [!NOTE]
     > Aby pomóc w debugowaniu aplikacji, jeśli wybierzesz **łącze Dziennika testów,** wynik testu sieci web lub wynik testu jednostkowego skojarzony z otwartym dziennikiem.

     Następnie można użyć operacji filtrowania i wyróżniania dostępnych na **wykresie aktywności użytkownika wirtualnego**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Aby użyć opcji filtrowania na wykresie aktywności użytkownika wirtualnego

1. Na liście **szczegółów**użyj listy rozwijanej, aby wybrać **opcję Testuj,** **Strona**lub **Transakcja**.

    **Panel Legenda szczegółów**

    ![Panel Legenda szczegółów](../test/media/ltest_detailslegend.png)

2. Zaznacz lub wyczyść pola wyboru dla błędów, dzienników, testów, wyszukiwania i stron aspx, które są skojarzone z testem obciążenia.

    **Wykres aktywności użytkownika wirtualnego** jest odpowiednio aktualizowany.

    **Wykres aktywności użytkownika wirtualnego** umożliwia odfiltrowanie testów, stron i transakcji na podstawie kilku różnych kryteriów. Można usunąć niektóre testy z widoku lub usunąć wszystkie pomyślne testy lub usunąć testy, które nie powiodły się z niektórych błędów. Można również usunąć wszystkie testy, które nie mają dzienników.

    Można na przykład wybrać opcję **(Wyróżnij błędy),** która wyświetla wszystkie błędy na wykresie w kolorze czerwonym. Można również wybrać opcję **(Wyróżnij wyniki z dziennikami),** która wyświetla wszystkie wyniki testów, które mają dzienniki kolorowe na zielono na wykresie.

    **Panel wyników filtrowania**

    ![Panel wyników filtrowania](../test/media/ltest_filterresults.png)

3. W **wynikach filtru**zaznacz lub wyczyść pola wyboru dla następujących opcji filtru:

   - **Pokaż tylko wyniki z dziennikami** Wyświetla tylko wyniki testów, które mają dzienniki testów skojarzone z nimi.

   - **Pokaż pomyślne wyniki** Wyświetla pomyślne wyniki.

   - **Pokaż wyniki z błędami** Wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

     > [!NOTE]
     > Listę typów błędów wymienionych w węźle **Pokaż wyniki z błędami** można dokładniej zbadać, wybierając przycisk **Tabele** na pasku narzędzi Podgląd wyników testów wydajności sieci **Web.** Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     **Wykres aktywności użytkownika wirtualnego** jest odpowiednio aktualizowany.

## <a name="see-also"></a>Zobacz też

- [Analizowanie aktywności użytkownika wirtualnego w widoku Szczegóły](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Instruktaż: Używanie wykresu aktywności użytkownika wirtualnego do izolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)