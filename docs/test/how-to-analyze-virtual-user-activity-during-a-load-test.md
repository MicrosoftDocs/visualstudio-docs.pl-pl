---
title: Analizowanie aktywności wirtualnego użytkownika testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: jillre
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dda1f35a63d3f7788faf9a94f16888c8323529c4
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091720"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Porady: analizowanie, co robią użytkownicy wirtualni podczas testu obciążenia za pomocą wykresu aktywności wirtualnego użytkownika

Wyświetl aktywność użytkownika wirtualnego skojarzoną z testem obciążenia za pomocą **wykresu aktywności wirtualnego użytkownika**. Każdy wiersz na wykresie reprezentuje poszczególnych użytkowników wirtualnych. **Wykres aktywność użytkownika wirtualnego** pokazuje, jak dokładnie każdy użytkownik wirtualny był wykonywany podczas testu. Można widać wzorce aktywności użytkowników, wzorce obciążenia, korelowanie testy zakończone niepowodzeniem lub wolne i zobacz żądań z innych działań wirtualnego użytkownika. **Wykres aktywności wirtualnego użytkownika** jest dostępny dopiero po zakończeniu testu obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W poniższych procedurach przedstawiono sposób wyświetlania **wykresu aktywności wirtualnego użytkownika**, sposobu badania aktywności określonego użytkownika i używania funkcji filtrowania.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby wyświetlić wykres aktywności wirtualnych użytkowników w wyniki testu obciążenia

1. Aby wyświetlić dane użytkownika wirtualnego, należy najpierw skonfigurować ustawienie **wszystkie szczegółowe informacje** dla właściwości **Magazyn szczegóły czasu** , która jest skojarzona z testem obciążenia. Następnie uruchom test obciążenia.

2. Po załadowaniu usługi przebiegów testów, zostanie wyświetlona strona podsumowania wyników testu. Wybierz przycisk **szczegóły użytkownika** na pasku narzędzi.

     —lub—

     Otwórz widok wykresy, wybierając przycisk **wykresy** na pasku narzędzi. Kliknij prawym przyciskiem myszy wykres, a następnie wybierz pozycję **Przejdź do szczegółów użytkownika**.

     Jeśli używasz tej opcji, **Wykres aktywności wirtualnego użytkownika** przejdzie do części testu, który został kliknięty prawym przyciskiem myszy. Na przykład, jeśli wskaźnik znajduje się około 30 sekund, widok szczegółów zostanie wyświetlony w przybliżeniu na 30 sekund w narzędziu **Powiększ do czasu** w dolnej części **wykresu wirtualnego aktywności użytkownika**.

     Następnie można zbadać szczegóły aktywności określonego użytkownika na **wykresie aktywności wirtualnego użytkownika**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Aby zbadać działania określonego użytkownika w wykres aktywności wirtualnych użytkowników

1. Użyj narzędzia Powiększ do okresu w dolnej części **wykresu aktywności wirtualnego użytkownika** , aby wybrać obszar wykresu, w którym chcesz zbadać szczegóły określonego użytkownika.

2. Umieść kursor myszy szczegółów na wykresie. Zwróć uwagę, że w etykietce narzędzia są wyświetlane następujące informacje:

   - **Identyfikator użytkownika**

   - **Scenariusz**

   - **Test**

   - **Adres URL** (nie jest wyświetlany w teście lub transakcji)

   - **Wynikiem**

   - **Przeglądarka** (nie jest wyświetlana w teście lub transakcji)

   - **Sieć**

   - **Godzina rozpoczęcia**

   - **Trwania**

   - **Agent**

   - **Dziennik testu** (link do dziennika testowego)

     > [!NOTE]
     > Aby pomóc w debugowaniu aplikacji, w przypadku wybrania linku **dziennika testowego** , wynik testu sieci Web lub wynik testu jednostkowego skojarzony z otwartym dziennikiem.

     Następnie można użyć operacji filtrowania i wyróżniania dostępnych na **wykresie wirtualnego działania użytkownika**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Aby użyć opcji filtrowania w wykres aktywności wirtualnych użytkowników

1. W **legendzie szczegółów**Użyj listy rozwijanej, aby wybrać **test**, **stronę**lub **transakcję**.

    **Panel legendy szczegółów**

    ![Legenda szczegółów — panel](../test/media/ltest_detailslegend.png)

2. Zaznacz lub wyczyść pola wyboru dla błędów, dzienniki, testy, wyszukiwania i stron aspx, które są skojarzone z testu obciążenia.

    **Wykres aktywności wirtualnego użytkownika** jest odpowiednio aktualizowany.

    **Wykres aktywności wirtualnego użytkownika** umożliwia filtrowanie testów, stron i transakcji na podstawie różnych kryteriów. Można usunąć niektórych testów w widoku lub Usuń wszystkie testy zakończone powodzeniem i usuwać testy, które nie powiodło się z pewnych błędów. Można również usunąć wszystkie testy, które nie mają dzienniki.

    Na przykład możesz wybrać opcję **(Wyróżnij błędy)** , która wyświetla wszystkie błędy na wykresie kolorem czerwonym. Możesz również wybrać opcję **(Wyróżnij wyniki z dziennikami)** , która wyświetla wszystkie wyniki testów, które mają w kolorze zielonym zieloną na wykresie.

    **Panel wyników filtrowania**

    ![Panel wyników filtrowania](../test/media/ltest_filterresults.png)

3. W **wynikach filtru**zaznacz lub usuń zaznaczenie pól wyboru dla następujących opcji filtru:

   - **Pokaż tylko wyniki z dziennikami** Wyświetla tylko wyniki testów, które mają skojarzone dzienniki testowe.

   - **Pokaż pomyślne wyniki** Wyświetla wyniki zakończone powodzeniem.

   - **Pokaż wyniki z błędami** Wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

     > [!NOTE]
     > Lista typów błędów, które są wymienione w węźle **Pokaż wyniki z błędami** , można dokładniej zbadać, wybierając przycisk **tabele** na pasku narzędzi **podglądu wyniki testów wydajności sieci Web** . Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     **Wykres aktywności wirtualnego użytkownika** jest odpowiednio aktualizowany.

## <a name="see-also"></a>Zobacz także

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Przewodnik: używanie wykresu aktywności wirtualnego użytkownika w celu wyizolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)