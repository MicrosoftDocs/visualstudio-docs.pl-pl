---
title: Czas reakcji strony w teście obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8bc1205658899a51cf1a50e83a9a8b34034b25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594338"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Jak: Wyświetlanie czasu reakcji strony sieci Web w teście obciążenia przy użyciu analizatora testów obciążenia

Czas ładowania każdej strony internetowej jest znany jako *czas reakcji.* Podczas tworzenia testu wydajności sieci Web, można ustawić cel czasu odpowiedzi dla każdego żądania strony sieci web w teście wydajności sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Jeśli uruchomisz test wydajności sieci Web pod wpływem stresu w teście obciążenia, będziesz mógł analizować następujące informacje dla każdej strony:

- Średni czas odpowiedzi dla strony.

- Procent iteracji testowych, które spełniają cel czasu odpowiedzi dla strony.

- Czasy odpowiedzi strony sieci Web można analizować za pomocą widoku Tabele lub widoku Wykresy w **analizatorze testów obciążenia:**

- Analizowanie czasów odpowiedzi strony sieci Web w widoku tabel

- Analizowanie czasów odpowiedzi strony sieci Web w widoku wykresów

## <a name="view-response-time-data-in-a-table"></a>Wyświetlanie danych czasu reakcji w tabeli

1. W **analizatorze testu obciążenia**wybierz **pozycję Tabele** na pasku narzędzi, aby upewnić się, że jest wyświetlana siatka tabeli.

2. Z listy rozwijanej **Tabela** wybierz pozycję **Strony**.

3. Dane dla każdej strony są wyświetlane w siatce. Następujące kolumny są zwykle wyświetlane.

   |Nagłówek kolumny|Opis|
   |-|-|
   |**Strona**|Nazwa strony internetowej.|
   |**Scenariusz**|Nazwa scenariusza. Ważne, jeśli masz więcej niż jeden scenariusz w teście wydajności sieci Web.|
   |**Test**|Nazwa testu wydajności sieci Web. Ważne, jeśli masz więcej niż jeden test wydajności sieci web w teście obciążenia.|
   |**Sieć**|Typ sieci.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytorze testów obciążenia**w węźle **Uruchom ustawienia** wybierz węzeł ustawień uruchamiania, aby zmienić. W oknie **Właściwości** dla właściwości **Magazyn szczegółów chronometrażu** wybierz pozycję **AllIndividualDetails**.|
   |**Łącznie**|Całkowita liczba żądań, które zostały wysłane dla strony sieci web. Jest to suma dla wszystkich iteracji w teście obciążenia.|
   |**Ave**|Średni czas odpowiedzi strony.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytorze testów obciążenia**w węźle **Uruchom ustawienia** wybierz węzeł ustawień uruchamiania, aby zmienić. W oknie **Właściwości** dla właściwości **Magazyn szczegółów chronometrażu** wybierz pozycję **AllIndividualDetails**.|
   |**Min**|Minimalny czas odpowiedzi strony.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytorze testów obciążenia**w węźle **Uruchom ustawienia** wybierz węzeł ustawień uruchamiania, aby zmienić. W oknie **Właściwości** dla właściwości **Magazyn szczegółów chronometrażu** wybierz pozycję **AllIndividualDetails**.|
   |**Mediana**|Mediana czasu odpowiedzi strony.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytorze testów obciążenia**w węźle **Uruchom ustawienia** wybierz węzeł ustawień uruchamiania, aby zmienić. W oknie **Właściwości** dla właściwości **Magazyn szczegółów chronometrażu** wybierz pozycję **AllIndividualDetails**.|
   |**90%**|90 percentyl dla czasu odpowiedzi. Oznacza to, że 90% stron odpowiedziało szybciej niż ta liczba, a 10% stron odpowiedziało wolniej.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytorze testów obciążenia**w węźle **Uruchom ustawienia** wybierz węzeł ustawień uruchamiania, aby zmienić. W oknie **Właściwości** dla właściwości **Magazyn szczegółów chronometrażu** wybierz pozycję **AllIndividualDetails**.|
   |**95%**|95 percentyl dla czasu odpowiedzi. Oznacza to, że 95% stron odpowiedziało szybciej niż ta liczba, a 5% stron odpowiedziało wolniej.|
   |**99%**|99 percentyl dla czasu odpowiedzi. Oznacza to, że 99% stron odpowiedziało szybciej niż ta liczba, a 1% stron odpowiedziało wolniej.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytorze testów obciążenia**w węźle **Uruchom ustawienia** wybierz węzeł ustawień uruchamiania, aby zmienić. W oknie **Właściwości** dla właściwości **Magazyn szczegółów chronometrażu** wybierz pozycję **AllIndividualDetails**.|
   |**Max**|Maksymalny czas odpowiedzi strony.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytorze testów obciążenia**w węźle **Uruchom ustawienia** wybierz węzeł ustawień uruchamiania, aby zmienić. W oknie **Właściwości** dla właściwości **Magazyn szczegółów chronometrażu** wybierz pozycję **AllIndividualDetails**.|
   |**Std Dev**|Domyślnie dane odchylenia standardowego nie są zbierane. Aby zebrać te dane, w **Edytorze testów obciążenia**w węźle **Uruchom ustawienia** wybierz węzeł ustawień uruchamiania, aby zmienić. W oknie **Właściwości** dla właściwości **Magazyn szczegółów chronometrażu** wybierz pozycję **AllIndividualDetails**.|
   |**Czas strony**|Średni czas odpowiedzi dla wszystkich żądań, które zostały wykonane dla strony internetowej.|
   |**Cel**|Cel czasu strony. Jest to stała wartość dla strony. **Uwaga:**  Cel czasu strony jest wyświetlany tylko wtedy, gdy cel został zdefiniowany dla żądania w teście wydajności sieci Web.|
   |**% celu spotkania**|Procent żądań, które zostały wykonane dla strony sieci web, która spełniła cel czasu odpowiedzi.|

   Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Wyświetlanie danych czasu reakcji na wykresie

Można również wyświetlić dane czasu odpowiedzi na wykresie, aby zobaczyć, jak zmienia się wraz z czasem podczas testu obciążenia. Jest to szczególnie przydatne, jeśli wzorzec obciążenia zwiększa się w miarę przebiegów testu (na przykład, jeśli używasz wzorca obciążenia kroku). Aby uzyskać więcej informacji, zobacz [Edytowanie wzorców obciążenia w celu modelowania działań użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Aby wyświetlić dane dotyczące czasu reakcji na wykresie:

1. W **analizatorze testu obciążenia**wybierz **wykresy** na pasku narzędzi, aby upewnić się, że wykres jest wyświetlany.

2. W oknie **Liczniki** rozwiń węzeł scenariusza, w którym jesteś `Scenario1`zainteresowany (na przykład ).

3. Rozwiń węzeł testu wydajności sieci web, w którym jesteś zainteresowany.

4. Rozwiń **strony**węzła .

5. Rozwiń węzeł strony, na której Cię interesuje.

6. Kliknij prawym przyciskiem myszy **pozycję % strony spotkania,** a następnie wybierz polecenie **Pokaż licznik na wykresie**.

    Dane są dodawane do wykresu.

7. (Opcjonalnie) Powtórz poprzedni krok dla **średnia czas strony,** **cel czasu reakcji strony**i całkowita liczba **stron**.

   > [!NOTE]
   > **Cel czasu reakcji strony** jest stały.

   Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku Wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
