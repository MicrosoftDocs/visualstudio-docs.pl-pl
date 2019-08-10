---
title: Parametry uruchomieniowe testu obciążenia
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4d50303596cec88bd5463b2ad1df713991c8932c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923675"
---
# <a name="load-test-run-settings-properties"></a>Właściwości ustawień przebiegu testu obciążenia

Parametry uruchomieniowe testu obciążenia określają różne inne ustawienia, w tym czas trwania testu, poziom szczegółowości kolekcji wyników i zestawy liczników, które są zbierane podczas przebiegu testu. Dla każdego testu obciążeniowego można utworzyć i zapisać wiele parametrów uruchomieniowych, a następnie wybrać jedno konkretne ustawienie do użycia podczas wykonywania testu. Początkowe ustawienie uruchomieniowe jest dodawane do testu obciążenia podczas tworzenia testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W poniższych tabelach opisano różne właściwości ustawień przebiegu testu obciążenia. Właściwości te można modyfikować, dopasowując do konkretnych wymagań dotyczących testowania obciążeniowego.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Właściwości ogólne

|Właściwość|Definicja|
|-|----------------|
|**Opis**|Opis parametrów uruchomieniowych.|
|**Maksymalna liczba błędów na typ**|Maksymalna liczba błędów na typ do zapisania w teście obciążenia.<br /><br /> Tę liczbę można zwiększyć, jeśli trzeba, ale spowoduje to również zwiększenie rozmiaru i czasu przetwarzania wyników testu obciążenia.|
|**Liczba raportowanych adresów URL żądań**|Maksymalna liczba unikatowych adresów URL żądań testu wydajności sieci Web, na których można raportować wyniki w tym teście obciążenia.<br /><br /> Tę liczbę można zwiększyć, jeśli trzeba, ale spowoduje to również zwiększenie rozmiaru i czasu przetwarzania wyników testu obciążenia.|
|**Maksymalne naruszenia progu**|Maksymalna liczba naruszeń progowych do zapisania dla tego testu obciążenia.<br /><br /> Tę liczbę można zwiększyć, jeśli trzeba, ale spowoduje to również zwiększenie rozmiaru i czasu przetwarzania wyników testu obciążenia.|
|**Uruchom testy jednostkowe w domenie aplikacji**|Wartość logiczna określająca, czy każdy zestaw testów jednostkowych będzie uruchamiany w oddzielnej domenie aplikacji, gdy test obciążenia zawiera testy jednostkowe. Ustawieniem domyślnym jest true.<br /><br /> Jeśli testy jednostkowe nie wymagają poprawnego działania osobnej domeny aplikacji lub pliku App. config, testy jednostkowe mogą działać szybciej, ustawiając wartość tej właściwości na `False`.|
|**Nazwa**|Nazwa ustawienia uruchomieniowego wyświetlanego w węźle **Parametry uruchomieniowe** **Edytor testu obciążeniowego**.|
|**Poziom walidacji**|Definiuje najwyższy poziom reguły walidacji, która będzie uruchamiana w teście obciążenia. Reguły walidacji są skojarzone z żądaniami testów wydajności sieci Web. Każda reguła walidacji ma skojarzony poziom walidacji: **Wysoki**, **Średni**lub **niski**. To ustawienie przebiegu testu obciążenia określa, które reguły walidacji będą uruchamiane, gdy test wydajności sieci Web zostanie uruchomiony w teście obciążenia. Jeśli na przykład to ustawienie uruchomieniowe ma wartość **średnia**, wszystkie reguły walidacji oznaczone jako **średnie**lub **niskie** zostaną uruchomione.|

## <a name="logging-properties"></a>Właściwości rejestrowania

|Właściwość|Definicja|
|-|----------------|
|**Maksymalna liczba dzienników testów**|Określa maksymalną liczbę dzienników testu do zapisania w teście obciążenia. Gdy zostanie osiągnięta maksymalna liczba dzienników testowych, test obciążenia zatrzyma zbieranie dzienników. W związku z tym dzienniki będą zbierane na początku testu, a nie na końcu. Test obciążenia będzie nadal wykonywany do momentu ukończenia.|
|**Zapisz częstotliwość rejestrowania dla zakończonych testów**|Określa częstotliwość, z jaką zostanie zapisany dziennik testowy. Liczba wskazuje, że jeden z każdej wprowadzonej liczby testów zostanie zapisany w dzienniku testu. Na przykład wprowadzenie wartości dziesięć określa, że dziesiąty, dwudziesty, 30 itd. zostanie zapisany w dzienniku testu. Ustawienie wartości 0 oznacza, że nie będą zapisywane dzienniki testowe.|
|**Zapisz dziennik podczas niepowodzenia testu**|Wartość logiczna określająca, czy dzienniki testów są zapisywane, jeśli test nie powiedzie się w teście obciążenia. Wartość domyślna to `True`.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Określ, czy niepowodzenia testu są zapisywane w dziennikach testów](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

Aby uzyskać więcej informacji, zobacz [Modyfikowanie ustawień rejestrowania testów obciążenia](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Właściwości wyników

|Właściwość|Definicja|
|-|----------------|
|**Typ magazynu**|Sposób przechowywania liczników wydajności uzyskanych w teście obciążenia. Dostępne są następujące opcje:<br /><br /> -   **Baza danych** — wymaga bazy danych SQL, która ma **Magazyn wyniki testów ładowania**.<br />-   **Brak**.|
|**Magazyn szczegółów czasu**|Służy do określania, które szczegóły będą przechowywane w **magazynie ładowania wyniki testów**. Dostępne są trzy wartości:<br /><br /> -   **AllIndividualDetails** — Zbieraj i przechowuj poszczególne wartości chronometrażu dla każdego testu, transakcji i strony, które zostały uruchomione lub wygenerowane podczas testu obciążenia w **magazynie wyniki testów obciążenia**. Jest to wymagane, jeśli zamierzasz używać **wykresu wirtualnego aktywności użytkownika** w **analizatorze testu obciążenia**.<br />     Aby uzyskać więcej informacji, zobacz [analizować aktywność wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Brak** — nie Zbieraj żadnych indywidualnych wartości chronometrażu. Jest to wartość domyślna dla Visual Studio 2013 Update 4 i nowszych wersji.<br />-   **StatisticsOnly** — Zbieraj i przechowuj tylko statystyki, zamiast przechowywać poszczególne wartości chronometrażu dla każdego testu, transakcji i strony, które zostały wykonane lub wygenerowane podczas testu obciążenia w **magazynie wyniki testów obciążenia**.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Określ właściwość](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)przechowywania informacji o chronometrażu.|

## <a name="sql-tracing-properties"></a>Właściwości śledzenia SQL

|Właściwość|Definicja|
|-|----------------|
|**Minimalny czas trwania śledzenia operacji SQL**|Minimalny czas trwania operacji SQL do przechwycenia przez śledzenie SQL w milisekundach. Umożliwia to na przykład ignorowanie operacji, które są wykonywane szybko, jeśli próbujesz znaleźć operacje SQL, które są wolniejsze pod obciążeniem.|
|**Ciąg połączenia śledzenia SQL**|Parametry połączenia, które są używane w celu uzyskania dostępu do bazy danych, która ma być śledzona.|
|**Katalog śledzenia SQL**|Lokalizacja, w której jest umieszczony plik śledzenia SQL po zakończeniu śledzenia. Ten katalog musi mieć uprawnienia do zapisu dla SQL Server i uprawnienia do odczytu kontrolera.|
|**Śledzenie SQL jest włączone**|Umożliwia to śledzenie operacji SQL. Wartość domyślna to `False`.|

## <a name="test-iterations-properties"></a>Właściwości iteracji testu

|Właściwość|Definicja|
|-|----------------|
|**Iteracje testu**|Określa łączną liczbę poszczególnych testów do uruchomienia przed ukończeniem testu obciążenia. Ta właściwość ma zastosowanie tylko wtedy, gdy właściwość "Użyj iteracji testowych" `True`ma wartość.|
|**Użyj iteracji testowych**|Jeśli Użyj iteracji `True`testowych, to test obciążenia jest uruchamiany do momentu, gdy liczba indywidualnych testów ukończonych w teście obciążenia osiągnie liczbę określoną przez właściwość "iteracje testów". W tym przypadku ustawienia czasu, które są czasochłonne, czas trwania przebiegu i czas chłodzenia, są ignorowane. Jeśli "Użyj iteracji testowych", wszystkie `False`ustawienia chronometrażu są stosowane i "iteracje testowe" jest ignorowana.|

Aby uzyskać więcej informacji, zobacz [jak: Określ liczbę iteracji testowych w ustawieniu](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)uruchomieniowym.

## <a name="timing-properties"></a>Właściwości chronometrażu

|Właściwość|Definicja|
|-|----------------|
|**Czas chłodzenia**|Czas trwania okresu chłodzenia testu wyrażony w formacie gg: mm: SS. Poszczególne testy w ramach testu obciążenia mogą nadal działać po zakończeniu testu obciążenia. W okresie chłodzenia te testy mogą być kontynuowane do momentu zakończenia lub osiągnięcia końca okresu chłodzenia. Domyślnie nie ma okresu chłodzenia, a poszczególne testy są przerywane po zakończeniu testu obciążenia na podstawie ustawienia czasu trwania przebiegu.|
|**Czas trwania przebiegu**|Długość testu, w formacie gg: mm: SS.|
|**Częstotliwość próbkowania**|Interwał przechwytywania wartości licznika wydajności w formacie gg: mm: SS.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Określ częstotliwość](../test/how-to-specify-the-sample-rate-for-a-load-test.md)próbkowania.|
|**Czas trwania rozgrzewania**|Okres między rozpoczęciem testu a rozpoczęciem rejestrowania próbek danych w formacie gg: mm: SS. Jest to często używane do kroku ładowania wirtualnych użytkowników w celu uzyskania dostępu do określonego poziomu obciążenia przed zarejestrowaniem przykładowych wartości. Przykładowe wartości, które są przechwytywane przed zakończeniem okresu rozgrzewania, są wyświetlane w **analizatorze testu obciążenia**.|

## <a name="webtest-connections-properties"></a>Właściwości połączeń WebTest

|Właściwość|Definicja|
|-|----------------|
|**Model połączeń WebTest**|Pozwala to kontrolować użycie połączeń z agenta testu obciążenia na serwerze sieci Web dla testów wydajności sieci Web, które są uruchamiane w ramach testu obciążenia. Dostępne są trzy opcje modelu połączenia testu wydajności sieci Web:<br /><br /> -Model **połączenie dla użytkownika** symuluje zachowanie użytkownika, który używa prawdziwej przeglądarki. Gdy program Internet Explorer 6 lub Internet Explorer 7 jest symulowany, każdy użytkownik wirtualny, który uruchamia test wydajności sieci Web, używa jednego lub dwóch dedykowanych połączeń z serwerem sieci Web. Pierwsze połączenie jest ustanawiane po wydaniu pierwszego żądania w teście wydajności sieci Web. Drugie połączenie może być używane, gdy strona zawiera więcej niż jedno żądanie zależne. Te żądania są emitowane równolegle przy użyciu dwóch połączeń. Te połączenia są ponownie używane na potrzeby kolejnych żądań w teście wydajności sieci Web. Połączenia są zamykane po zakończeniu testu wydajności sieci Web. Wadą tego modelu jest to, że liczba połączeń, które są otwarte na komputerze agenta, może być wysoka (maksymalnie dwa razy obciążenie użytkownikami). W związku z tym zasoby, które są wymagane do obsługi tej liczby połączeń, mogą ograniczyć obciążenie użytkownikami, które mogą być sterowane przez pojedynczy agent testu obciążenia. Gdy program Internet Explorer 8 jest symulowany, obsługiwane są sześć współbieżnych połączeń.<br />-Model **puli połączeń** zachowuje zasoby w agencie testu obciążenia przez udostępnienie połączeń z serwerem sieci Web wśród wielu wirtualnych użytkowników testów wydajności sieci Web. Jeśli obciążenie użytkownikami jest większe niż rozmiar puli połączeń, testy wydajności sieci Web, które są uruchamiane przez różnych użytkowników wirtualnych, będą współdzielić połączenie. Może to oznaczać, że jeden test wydajności sieci Web może upłynąć do momentu wypróbowania żądania, gdy inny test wydajności sieci Web używa połączenia. Średni czas oczekiwania testu wydajności sieci Web przed przesłaniem żądania jest śledzony przez średni czas oczekiwania połączenia licznika wydajności testu obciążenia. Ta wartość powinna być mniejsza niż średni czas odpowiedzi dla strony. Jeśli tak nie jest, rozmiar puli połączeń jest prawdopodobnie zbyt mały.<br />- **Połączenie na model iteracji testu** określa użycie dedykowanych połączeń dla każdej iteracji testu.|
|**Rozmiar puli połączeń WebTest**|Określa maksymalną liczbę połączeń między agentem testu obciążenia a serwerem sieci Web. Dotyczy to tylko modelu **puli połączeń** .|

## <a name="change-run-setting-properties"></a>Zmień właściwości ustawienia uruchomieniowego

Do testu obciążeniowego można dodać więcej parametrów uruchomieniowych z różnymi ustawieniami właściwości, co pozwoli wykonywać te testy w różnych warunkach. Na przykład można dodać nowe ustawienie testu określające inną częstotliwość próbkowania albo dłuższy czas trwania. Można używać tylko jednego ustawienia uruchomieniowego naraz i należy określić, które ustawienie uruchomieniowe ma być używane, oznaczając je jako aktywne. Aby zapoznać się z przykładem, zobacz [How to: Wybierz aktywne ustawienie uruchomieniowe dla testu](../test/how-to-select-the-active-run-setting-for-a-load-test.md)obciążenia.

Aby zmienić Parametry uruchomieniowe:

1. Otwórz test obciążenia.

2. Rozwiń **parametrów uruchomieniowych** folderu.

3. Wybierz węzeł **Parametry uruchomieniowe** .

4. Na **widoku** menu, wybierz **okno właściwości**.

     Zostanie wyświetlone **okno właściwości** , w którym są wyświetlane właściwości wybranego ustawienia uruchomieniowego.

5. Użyj **okna właściwości** , aby zmienić ustawienia uruchomieniowe. Na przykład zmienić czas trwania testu na **00:05:00** Aby uruchomić test na pięć minut.

    > [!NOTE]
    > Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawienia przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

6. Po zakończeniu zmiany właściwości Zapisz test obciążenia. W menu **plik** wybierz polecenie **Zapisz**.

> [!NOTE]
> Mapowania zestawu liczników są również częścią parametrów uruchomieniowych. Aby uzyskać więcej informacji, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)