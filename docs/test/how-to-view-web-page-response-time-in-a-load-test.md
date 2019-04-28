---
title: Czas odpowiedzi strony w teście obciążeniowym
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed1bd922b390d5b6e90c68b08683e1b9bdb46f32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821251"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Instrukcje: Czas odpowiedzi strony sieci web widoku w teście obciążenia za pomocą analizatora testu obciążenia

Czas potrzebny na każdej stronie sieci web załadować jest znany jako *czas odpowiedzi*. Podczas tworzenia testu wydajności sieci web, można ustawić docelowy czas odpowiedzi dla każdego żądania strony sieci web w teście wydajności sieci web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Po uruchomieniu testu wydajności sieci web przy dużym obciążeniu w teście obciążeniowym, możliwe będzie analizowanie następujących informacji dla każdej strony:

- Średni czas odpowiedzi dla strony.

- Procent iteracji testowych, które spełniają docelowy czas odpowiedzi dla strony.

- Czasy reakcji stron sieci web można analizować za pomocą widoku tabeli lub widoku wykresu w **analizatora testu obciążenia**:

- Analizowanie czasy reakcji stron sieci web w widoku tabeli

- Analizowanie czasy reakcji stron sieci web w widoku wykresu

## <a name="view-response-time-data-in-a-table"></a>Wyświetl dane czasu odpowiedzi w tabeli

1. W **analizatora testu obciążenia**, wybierz **tabel** na pasku narzędzi, aby upewnić się, że wyświetlana jest siatka tabeli.

2. W **tabeli** listy rozwijanej wybierz pozycję **stron**.

3. Dane dla każdej strony są wyświetlane w siatce. Zazwyczaj są wyświetlane następujące kolumny.

   |Nagłówek kolumny|Opis|
   |-|-|
   |**Strona**|Nazwa strony sieci web.|
   |**Scenariusz**|Nazwa scenariusza. Ważne, jeśli masz więcej niż jeden scenariusz w teście wydajności sieci web.|
   |**Test**|Nazwa testu wydajności sieci web. Ważne, jeśli masz więcej niż jeden wydajności sieci web, testu w teście obciążenia.|
   |**Sieci**|Typ sieci.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
   |**Łączna liczba**|Całkowita liczba żądań, które zostały wprowadzone dla strony sieci web. Jest to suma dla wszystkich iteracji w teście obciążeniowym.|
   |**Zapisz**|Średniego czasu odpowiedzi strony.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
   |**Min**|Czas odpowiedzi strony minimalnej.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
   |**Mediana**|Mediana czasu odpowiedzi strony na.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
   |**90%**|90. percentyla dla czasu odpowiedzi. To wskazuje, że 90% stron szybciej niż ta liczba wysłanych jako odpowiedzi i 10% stron odpowiedzi wolniej.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
   |**95%**|95. percentyl czasu odpowiedzi. To wskazuje, że 95% stron szybciej niż ta liczba wysłanych jako odpowiedzi i 5 procent stron odpowiedzi wolniej.|
   |**99%**|99. percentylu na czas odpowiedzi. Oznacza to, że 99% stron szybciej niż ta liczba wysłanych jako odpowiedzi, a 1% stron odpowiedzi wolniej.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
   |**Maksymalna**|Strona maksymalny czas odpowiedzi.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
   |**Odchylenie standardowe**|Domyślnie nie są zbierane dane odchylenia standardowego. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
   |**Czas strony**|Średni czas odpowiedzi dla wszystkich żądań, które zostały wprowadzone dla strony sieci web.|
   |**Cel**|Cel dotyczący czasu strony. Jest to wartość stałą dla strony. **Uwaga:**  Cel dotyczący czasu strona jest wyświetlana tylko wtedy, gdy celem został zdefiniowany dla żądania w teście wydajności sieci web.|
   |**% Osiągnięcia celu**|Procent żądań, które zostały wprowadzone na stronie sieci web, że zostały spełnione cel dotyczący czasu odpowiedzi.|

   Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Wyświetl dane czasu odpowiedzi w formie wykresu

Można również wyświetlić dane czasu odpowiedzi na wykresie, aby zobaczyć, jak zmienia się wraz z upływem czasu podczas testu obciążenia. Jest to szczególnie przydatne, jeśli Twoja wzorca obciążenia zwiększa się po uruchomieniu testów (na przykład, jeśli używasz krokowego wzorca obciążenia). Aby uzyskać więcej informacji, zobacz [obciążenia Edytowanie wzorców do działań wirtualnego użytkownika w modelu](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Aby wyświetlić dane czasu odpowiedzi w postaci wykresu:

1. W **analizatora testu obciążenia**, wybierz **wykresów** na pasku narzędzi, aby upewnić się, czy są wyświetlane na wykresie.

2. W **liczniki** okna, rozwiń węzeł scenariusz, w którym interesuje Cię (na przykład `Scenario1`).

3. Rozwiń węzeł testu wydajności sieci web, w którym interesuje Cię.

4. Rozwiń węzeł **stron**.

5. Rozwiń węzeł strony, w którym interesuje Cię.

6. Kliknij prawym przyciskiem myszy **% stron osiągnięcia celu** , a następnie wybierz **Pokaż licznik na wykresie**.

    Dane są dodawane do grafu.

7. (Opcjonalnie) Powtórz poprzedni krok dla **średni Czas strony**, **cel dotyczący czasu odpowiedzi strony**, i **łączna liczba stron**.

   > [!NOTE]
   > **Cel dotyczący czasu odpowiedzi strony** jest stały.

   Aby uzyskać więcej informacji, zobacz [w widoku wykresu z wynikami testów obciążeniowych analizy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Instrukcje: Wyniki testu obciążeniowego dostęp do analizy](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)