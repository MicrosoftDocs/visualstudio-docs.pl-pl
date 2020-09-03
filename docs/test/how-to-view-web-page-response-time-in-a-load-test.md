---
title: Czas odpowiedzi strony w teście obciążenia
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1affda002290a191fde6d5115094a2185ac8bfcb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287054"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Instrukcje: wyświetlanie czasu odpowiedzi strony sieci Web w teście obciążenia za pomocą analizatora testu obciążenia

Czas potrzebny na załadowanie każdej strony sieci Web jest znany jako *czas odpowiedzi*. Podczas tworzenia testu wydajności sieci Web można ustawić cel czasu odpowiedzi dla każdego żądania strony sieci Web w teście wydajności sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Jeśli uruchomisz test wydajności sieci Web w ramach obciążenia w teście obciążeniowym, będzie można analizować następujące informacje dotyczące poszczególnych stron:

- Średni czas odpowiedzi dla strony.

- Procent iteracji testowych, które spełniają cel czasu odpowiedzi dla strony.

- Czasy odpowiedzi strony sieci Web można analizować za pomocą widoku tabele lub widoku wykresy w **analizatorze testu obciążenia**:

- Analizowanie czasów odpowiedzi stron sieci Web w widoku tabel

- Analizowanie czasów odpowiedzi stron sieci Web w widoku wykresy

## <a name="view-response-time-data-in-a-table"></a>Wyświetlanie danych czasu odpowiedzi w tabeli

1. W **analizatorze testu obciążenia**wybierz **tabele** na pasku narzędzi, aby upewnić się, że jest wyświetlana siatka tabeli.

2. W polu listy rozwijanej **tabela** wybierz pozycję **strony**.

3. W siatce zostanie wyświetlona data dla każdej strony. Wyświetlane są zwykle następujące kolumny.

   |Nagłówek kolumny|Opis|
   |-|-|
   |**Strona**|Nazwa strony sieci Web.|
   |**Scenariusz**|Nazwa scenariusza. Ważne, jeśli masz więcej niż jeden scenariusz w teście wydajności sieci Web.|
   |**Test**|Nazwa testu wydajności sieci Web. Ważne, jeśli masz więcej niż jeden test wydajności sieci Web w teście obciążenia.|
   |**Sieć**|Typ sieci.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytor testu obciążeniowego**w węźle **Parametry uruchomieniowe** wybierz węzeł ustawienie uruchomieniowe, które ma zostać zmienione. W oknie **Właściwości** dla właściwości **Magazyn szczegóły czasu** wybierz pozycję **AllIndividualDetails**.|
   |**Łącznie**|Całkowita liczba żądań, które zostały wykonane dla strony sieci Web. Jest to suma wszystkich iteracji w teście obciążenia.|
   |**Ave**|Średni czas odpowiedzi strony.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytor testu obciążeniowego**w węźle **Parametry uruchomieniowe** wybierz węzeł ustawienie uruchomieniowe, które ma zostać zmienione. W oknie **Właściwości** dla właściwości **Magazyn szczegóły czasu** wybierz pozycję **AllIndividualDetails**.|
   |**Długości**|Minimalny czas odpowiedzi strony.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytor testu obciążeniowego**w węźle **Parametry uruchomieniowe** wybierz węzeł ustawienie uruchomieniowe, które ma zostać zmienione. W oknie **Właściwości** dla właściwości **Magazyn szczegóły czasu** wybierz pozycję **AllIndividualDetails**.|
   |**Mediana**|Średni czas odpowiedzi strony.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytor testu obciążeniowego**w węźle **Parametry uruchomieniowe** wybierz węzeł ustawienie uruchomieniowe, które ma zostać zmienione. W oknie **Właściwości** dla właściwości **Magazyn szczegóły czasu** wybierz pozycję **AllIndividualDetails**.|
   |**90%**|90. percentyl dla czasu odpowiedzi. Oznacza to, że 90% stron odpowiada szybciej niż ta liczba, a 10% stron reaguje wolniej.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytor testu obciążeniowego**w węźle **Parametry uruchomieniowe** wybierz węzeł ustawienie uruchomieniowe, które ma zostać zmienione. W oknie **Właściwości** dla właściwości **Magazyn szczegóły czasu** wybierz pozycję **AllIndividualDetails**.|
   |**95%**|Używany 95. percentyl na czas odpowiedzi. Oznacza to, że 95% stron odpowiada szybciej niż ta liczba, a 5% stron reaguje wolniej.|
   |**99%**|99 percentyl na czas odpowiedzi. Oznacza to, że 99% stron odpowiada szybciej niż ta liczba, a 1% stron reaguje wolniej.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytor testu obciążeniowego**w węźle **Parametry uruchomieniowe** wybierz węzeł ustawienie uruchomieniowe, które ma zostać zmienione. W oknie **Właściwości** dla właściwości **Magazyn szczegóły czasu** wybierz pozycję **AllIndividualDetails**.|
   |**Maksymalny**|Maksymalny czas odpowiedzi strony.<br /><br /> Domyślnie te dane nie są zbierane. Aby zebrać te dane, w **Edytor testu obciążeniowego**w węźle **Parametry uruchomieniowe** wybierz węzeł ustawienie uruchomieniowe, które ma zostać zmienione. W oknie **Właściwości** dla właściwości **Magazyn szczegóły czasu** wybierz pozycję **AllIndividualDetails**.|
   |**Odchylenie standardowe**|Domyślnie dane odchylenia standardowego nie są zbierane. Aby zebrać te dane, w **Edytor testu obciążeniowego**w węźle **Parametry uruchomieniowe** wybierz węzeł ustawienie uruchomieniowe, które ma zostać zmienione. W oknie **Właściwości** dla właściwości **Magazyn szczegóły czasu** wybierz pozycję **AllIndividualDetails**.|
   |**Czas strony**|Średni czas odpowiedzi dla wszystkich żądań, które zostały wykonane dla strony sieci Web.|
   |**Cel**|Cel czasu strony. Jest to stała wartość dla strony. **Uwaga:**  Cel czasu strony jest wyświetlany tylko wtedy, gdy cel został zdefiniowany dla żądania w teście wydajności sieci Web.|
   |**% Celu spotkania**|Procent żądań, które zostały wykonane dla strony sieci Web, która osiągnęła cel czasu odpowiedzi.|

   Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Wyświetlanie danych czasu odpowiedzi w grafie

Możesz również wyświetlić dane czasu odpowiedzi w grafie, aby zobaczyć, jak zmienia się w czasie testu obciążenia. Jest to szczególnie przydatne, Jeśli wzorzec obciążenia rośnie wraz z przebiegami testów (na przykład w przypadku użycia krokowego wzorca obciążenia). Aby uzyskać więcej informacji, zobacz [Edytowanie wzorców ładowania do modelu aktywności użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Aby wyświetlić dane czasu odpowiedzi w grafie:

1. W **analizatorze testu obciążenia**wybierz **wykresy** na pasku narzędzi, aby upewnić się, że wykres jest wyświetlany.

2. W oknie **liczniki** rozwiń węzeł scenariusza, w którym Cię interesuje (na przykład `Scenario1` ).

3. Rozwiń węzeł testu wydajności sieci Web, w którym Cię interesujesz.

4. Rozwiń węzeł **strony**.

5. Rozwiń węzeł interesującej strony.

6. Kliknij prawym przyciskiem myszy pozycję **% stron na spotkaniu** , a następnie wybierz polecenie **Pokaż licznik na grafie**.

    Dane są dodawane do grafu.

7. Obowiązkowe Powtórz poprzedni krok dla **średniego czasu strony**, **celu czasu odpowiedzi strony**i **łącznej liczby stron**.

   > [!NOTE]
   > **Cel czasu odpowiedzi strony** jest stały.

   Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testów obciążenia i błędów w widoku tabel](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Instrukcje: uzyskiwanie dostępu do wyników testu obciążenia na potrzeby analizy](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
