---
title: Analizowanie aktywności wirtualnego użytkownika na potrzeby testów obciążenia
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64b69ba926e3c978efa60bd9946da94d846c383f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288406"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Instrukcje: analizowanie, co robią Użytkownicy wirtualną podczas testu obciążenia za pomocą wykresu aktywności wirtualnego użytkownika

Wyświetl aktywność użytkownika wirtualnego skojarzoną z testem obciążenia za pomocą **wykresu aktywności wirtualnego użytkownika**. Każdy wiersz na wykresie reprezentuje pojedynczego użytkownika wirtualnego. **Wykres aktywność użytkownika wirtualnego** pokazuje, jak dokładnie każdy użytkownik wirtualny był wykonywany podczas testu. Można zobaczyć wzorce aktywności użytkownika, wzorce obciążenia, skorelować Niepowodzenie lub powolne testy i zobaczyć żądania z innymi wirtualnymi działaniami użytkowników. **Wykres aktywności wirtualnego użytkownika** jest dostępny dopiero po zakończeniu testu obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W poniższych procedurach przedstawiono sposób wyświetlania **wykresu aktywności wirtualnego użytkownika**, sposobu badania aktywności określonego użytkownika i używania funkcji filtrowania.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby wyświetlić wykres aktywności wirtualnego użytkownika w wynikach testu obciążenia

1. Aby wyświetlić dane użytkownika wirtualnego, należy najpierw skonfigurować ustawienie **wszystkie szczegółowe informacje** dla właściwości **Magazyn szczegóły czasu** , która jest skojarzona z testem obciążenia. Następnie uruchom test obciążenia.

2. Po uruchomieniu testu obciążenia zostanie wyświetlona strona podsumowanie wyników testu. Wybierz przycisk **szczegóły użytkownika** na pasku narzędzi.

     -lub-

     Otwórz widok wykresy, wybierając przycisk **wykresy** na pasku narzędzi. Kliknij prawym przyciskiem myszy wykres, a następnie wybierz pozycję **Przejdź do szczegółów użytkownika**.

     Jeśli używasz tej opcji, **Wykres aktywności wirtualnego użytkownika** przejdzie do części testu, który został kliknięty prawym przyciskiem myszy. Na przykład, jeśli wskaźnik znajduje się około 30 sekund, widok szczegółów zostanie wyświetlony w przybliżeniu na 30 sekund w narzędziu **Powiększ do czasu** w dolnej części **wykresu wirtualnego aktywności użytkownika**.

     Następnie można zbadać szczegóły aktywności określonego użytkownika na **wykresie aktywności wirtualnego użytkownika**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Aby zbadać aktywność określonego użytkownika na wykresie aktywności wirtualnego użytkownika

1. Użyj narzędzia Powiększ do okresu w dolnej części **wykresu aktywności wirtualnego użytkownika** , aby wybrać obszar wykresu, w którym chcesz zbadać szczegóły określonego użytkownika.

2. Umieść wskaźnik myszy nad szczegółowym wykresem. Zwróć uwagę, że następujące informacje są wyświetlane w etykietce narzędzia:

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

   - **Dziennik testu** (link do dziennika testowego)

     > [!NOTE]
     > Aby pomóc w debugowaniu aplikacji, w przypadku wybrania linku **dziennika testowego** , wynik testu sieci Web lub wynik testu jednostkowego skojarzony z otwartym dziennikiem.

     Następnie można użyć operacji filtrowania i wyróżniania dostępnych na **wykresie wirtualnego działania użytkownika**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Aby użyć opcji filtrowania na wykresie aktywności wirtualnego użytkownika

1. W **legendzie szczegółów**Użyj listy rozwijanej, aby wybrać **test**, **stronę**lub **transakcję**.

    **Panel legendy szczegółów**

    ![Panel legendy szczegółów](../test/media/ltest_detailslegend.png)

2. Zaznacz lub wyczyść pola wyboru dla błędów, dzienników, testów, wyszukiwania i stron aspx, które są skojarzone z testem obciążenia.

    **Wykres aktywności wirtualnego użytkownika** jest odpowiednio aktualizowany.

    **Wykres aktywności wirtualnego użytkownika** umożliwia filtrowanie testów, stron i transakcji na podstawie różnych kryteriów. Można usunąć niektóre testy z widoku lub usunąć wszystkie testy zakończone powodzeniem lub usunąć testy, które zakończyły się niepowodzeniem z pewnymi błędami. Można również usunąć wszystkie testy, które nie mają dzienników.

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

## <a name="see-also"></a>Zobacz też

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Przewodnik: używanie wykresu aktywności wirtualnego użytkownika w celu wyizolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)