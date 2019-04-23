---
title: Analizowanie aktywności wirtualnego użytkownika testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dadc35d09ad70986f728104396502f13a06c0995
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079464"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Instrukcje: Analizowanie, co robią użytkownicy wirtualni podczas testu obciążenia za pomocą wykresu aktywności wirtualnego użytkownika

Wyświetl aktywność wirtualnego użytkownika skojarzonego z testu obciążenia przy użyciu **wykres aktywności wirtualnych użytkowników**. Każdy wiersz na wykresie reprezentuje poszczególnych użytkowników wirtualnych. **Wykres aktywności wirtualnych użytkowników** dowiesz się, dokładnie co każdy użytkownik wirtualny był wykonywany podczas testu. Można widać wzorce aktywności użytkowników, wzorce obciążenia, korelowanie testy zakończone niepowodzeniem lub wolne i zobacz żądań z innych działań wirtualnego użytkownika. **Wykres aktywności wirtualnych użytkowników** jest dostępna tylko w przypadku, po zakończeniu testu obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Poniższe procedury pokazują, jak wyświetlić **wykres aktywności wirtualnych użytkowników**, jak Zbadaj działania konkretnego użytkownika i jak używać filtrowania.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Aby wyświetlić wykres aktywności wirtualnych użytkowników w wyniki testu obciążenia

1. Aby wyświetlić dane użytkowników wirtualnych, należy najpierw skonfigurować **wszystkie szczegółowe dane** ustawienie **przechowywanie informacji** właściwość, która jest skojarzona z testu obciążenia. Następnie uruchom test obciążenia.

2. Po załadowaniu usługi przebiegów testów, zostanie wyświetlona strona podsumowania wyników testu. Wybierz **szczegółów użytkownika** przycisk na pasku narzędzi.

     —lub—

     Otwórz widok wykresów, wybierając **wykresów** przycisk na pasku narzędzi. Kliknij prawym przyciskiem myszy wykres, a następnie wybierz pozycję **przejdź do szczegółów użytkownika**.

     Jeśli używasz tej opcji **wykres aktywności wirtualnych użytkowników** spowoduje automatyczne powiększanie części testu, który kliknięcia prawym przyciskiem. Na przykład, jeśli wskaźnik myszy znajduje się na około 30 drugim znaku, widok szczegółów wyświetli około na 30 drugim znaku w **Powiększ do okresu czasu** narzędzia w dolnej części **wykres aktywności wirtualnych użytkowników** .

     Następnie można zbadać szczegóły aktywności użytkowników w **wykres aktywności wirtualnych użytkowników**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Aby zbadać działania określonego użytkownika w wykres aktywności wirtualnych użytkowników

1. Polecenie narzędzia okresu czasu w dolnej części **wykres aktywności wirtualnych użytkowników** aby wybrać obszar na wykresie, w którym chcesz zbadać szczegółowe informacje na temat określonego użytkownika.

2. Umieść kursor myszy szczegółów na wykresie. Zwróć uwagę, że w etykietce narzędzia są wyświetlane następujące informacje:

   - **Identyfikator użytkownika**

   - **Scenariusz**

   - **Test**

   - **Adres URL** (nie jest wyświetlane w testowej lub transakcji)

   - **Wynik**

   - **Przeglądarka** (nie jest wyświetlane w testowej lub transakcji)

   - **Sieci**

   - **Godzina rozpoczęcia**

   - **Czas trwania**

   - **Agent**

   - **Dziennik testu** (łącze do dziennika testu)

     > [!NOTE]
     > Aby pomóc w debugowaniu aplikacji, jeśli wybierzesz **Dziennik testu** łącze, wynik testu sieci web lub wynik skojarzony z Otwórz dziennik testu jednostkowego.

     Następnie można użyć filtrowania i wyróżniania operacje dostępne w **wykres aktywności wirtualnych użytkowników**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Aby użyć opcji filtrowania w wykres aktywności wirtualnych użytkowników

1. W **Legenda szczegółów**, użyj listy rozwijanej możesz wybrać opcję **testu**, **strony**, lub **transakcji**.

    **Legenda szczegółów — panel**

    ![Legenda szczegółów — panel](../test/media/ltest_detailslegend.png)

2. Zaznacz lub wyczyść pola wyboru dla błędów, dzienniki, testy, wyszukiwania i stron aspx, które są skojarzone z testu obciążenia.

    **Wykres aktywności wirtualnych użytkowników** odpowiednio aktualizowany.

    **Wykres aktywności wirtualnych użytkowników** umożliwia filtrowanie testy, strony i transakcje na podstawie kilku różnych kryteriów. Można usunąć niektórych testów w widoku lub Usuń wszystkie testy zakończone powodzeniem i usuwać testy, które nie powiodło się z pewnych błędów. Można również usunąć wszystkie testy, które nie mają dzienniki.

    Na przykład, możesz wybrać **(Podświetl błędy)** opcja, która wyświetla wszystkie błędy na wykresie pokolorowane w kolorze czerwonym. Możesz również wybrać **(Podświetl wyniki z dziennikami)** opcja, która wyświetla wszystkie wyniki testów, które mają dzienniki pokolorowane w kolorze zielonym na wykresie.

    **Panel wyników filtrowania**

    ![Panel wyników filtrowania](../test/media/ltest_filterresults.png)

3. W **filtrowanie wyników**, zaznacz lub wyczyść pola wyboru dla następujących opcji filtrowania:

   - **Pokaż tylko wyniki z dziennikami** wyświetla tylko wyniki, które mają dzienniki testów skojarzonych z nimi.

   - **Pokaż pomyślne wyniki** Wyświetla pomyślne wyniki.

   - **Pokaż wyniki z błędami** wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

     > [!NOTE]
     > Lista typów błędów, które są wyświetlane w obszarze **Pokaż wyniki z błędami** węzła może dalszego zbadania, wybierając **tabel** znajdujący się w **podgląduwynikówtestuwydajnościsieciWeb** paska narzędzi. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     **Wykres aktywności wirtualnych użytkowników** odpowiednio aktualizowany.

## <a name="see-also"></a>Zobacz także

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Przewodnik: Za pomocą wykresu aktywności wirtualnego użytkownika umożliwiającego Wyizolowanie problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)