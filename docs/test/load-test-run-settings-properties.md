---
title: Parametry uruchomieniowe testu obciążenia
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8898a474888ce9efbf4c91a5251bf8fe7036fe5f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584468"
---
# <a name="load-test-run-settings-properties"></a>Właściwości ustawień przebiegu testu obciążenia

Ustawienia uruchamiania testu obciążenia określają wiele innych ustawień, w tym czas trwania testu, poziom szczegółowości kolekcji wyników i zestawy liczników, które są zbierane podczas uruchamiania testu. Dla każdego testu obciążeniowego można utworzyć i zapisać wiele parametrów uruchomieniowych, a następnie wybrać jedno konkretne ustawienie do użycia podczas wykonywania testu. Ustawienie początkowego uruchomienia jest dodawane do testu obciążenia podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W poniższych tabelach opisano różne właściwości ustawień przebiegu testu obciążenia. Właściwości te można modyfikować, dopasowując do konkretnych wymagań dotyczących testowania obciążeniowego.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Właściwości ogólne

|Właściwość|Definicja|
|-|----------------|
|**Opis**|Opis ustawienia uruchamiania.|
|**Maksymalny błąd na typ**|Maksymalna liczba błędów na typ, aby zapisać dla testu obciążenia.<br /><br /> Można zwiększyć tę liczbę, jeśli trzeba, ale w ten sposób zwiększy również rozmiar i czas przetwarzania wyniku testu obciążenia.|
|**Maksymalne zgłoszone adresy URL żądań**|Maksymalna liczba unikatowych adresów URL żądań testu wydajności sieci Web, na których mają być raportować wyniki tego testu obciążenia.<br /><br /> Można zwiększyć tę liczbę, jeśli trzeba, ale w ten sposób zwiększy również rozmiar i czas przetwarzania wyniku testu obciążenia.|
|**Maksymalne naruszenia progu**|Maksymalna liczba naruszeń progu do zapisania dla tego testu obciążenia.<br /><br /> Można zwiększyć tę liczbę, jeśli trzeba, ale w ten sposób zwiększy również rozmiar i czas przetwarzania wyniku testu obciążenia.|
|**Uruchamianie testów jednostkowych w domenie aplikacji**|Wartość logiczna, która określa, czy każdy zestaw testu jednostkowego będzie uruchamiany w osobnej domenie aplikacji, gdy test obciążenia zawiera testy jednostkowe. Domyślnym ustawieniem jest Prawda.<br /><br /> Jeśli testy jednostkowe nie wymagają poprawnego działania oddzielnej domeny aplikacji lub pliku app.config, testy `False`jednostkowe mogą działać szybciej, ustawiając wartość tej właściwości na .|
|**Nazwa**|Nazwa ustawienia uruchamiania wyświetlana w węźle **Uruchom ustawienia** **Edytora testów obciążenia**.|
|**Poziom sprawdzania poprawności**|Definiuje najwyższy poziom reguły sprawdzania poprawności, która zostanie uruchomiony w teście obciążenia. Reguły sprawdzania poprawności są skojarzone z żądaniami testu wydajności sieci web. Każda reguła sprawdzania poprawności ma skojarzony poziom sprawdzania poprawności: **Wysoki,** **Średni**lub **Niski**. To ustawienie przebiegu testu obciążenia określi, które reguły sprawdzania poprawności będą uruchamiane, gdy test wydajności sieci web jest uruchamiany w teście obciążenia. Jeśli na przykład ustawienie uruchamiania jest ustawione na **Średni,** zostaną uruchomione wszystkie reguły sprawdzania poprawności oznaczone jako **Średnie**lub **Niskie.**|

## <a name="logging-properties"></a>Właściwości rejestrowania

|Właściwość|Definicja|
|-|----------------|
|**Maksymalna liczba dzienników testów**|Określa maksymalną liczbę dzienników testów do zapisania dla testu obciążenia. Po osiągnięciu wartości wprowadzonej dla maksymalnej liczby dzienników testów test zostanie zatrzymany, aby zatrzymać zbieranie dzienników. W związku z tym dzienniki zostaną zebrane na początku testu, a nie na końcu. Test obciążenia będzie nadal działać do momentu jego zakończenia.|
|**Zapisz częstotliwość dzienników dla zakończonych testów**|Określa częstotliwość, z jaką zostanie zapisany dziennik testu. Liczba wskazuje, że jedna z każdej wprowadzonej liczby testów zostanie zapisana w dzienniku testów. Na przykład wprowadzenie wartości dziesięciu określa, że dziesiąta, dwudziesta, trzydziesta i tak dalej zostanie zapisana w dzienniku testów. Ustawienie wartości 0 określa, że nie zostaną zapisane żadne dzienniki testów.|
|**Zapisz błąd testu logowania**|Wartość logiczna, która określa, czy jeśli dzienniki testów są zapisywane, jeśli test zakończy się niepowodzeniem w teście obciążenia. Wartość domyślna to `True`.<br /><br /> Aby uzyskać więcej informacji, zobacz [Jak: Określanie, czy błędy testu są zapisywane w dziennikach testowych](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

Aby uzyskać więcej informacji, zobacz [Modyfikowanie ustawień rejestrowania testu obciążenia](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Właściwości wyników

|Właściwość|Definicja|
|-|----------------|
|**Typ magazynu**|Sposób przechowywania liczników wydajności, które są uzyskiwane w teście obciążenia. Dostępne są następujące opcje:<br /><br /> -   **Baza danych** — wymaga bazy danych SQL, która ma **magazyn wyników testu obciążenia**.<br />-   **Brak**.|
|**Przechowywanie szczegółów chronometrażu**|Służy to do określenia, które szczegóły będą przechowywane w **magazynie wyników testów obciążenia.** Dostępne są trzy wartości:<br /><br /> -   **AllIndividualDetails** — zbieraj i przechowuj indywidualne wartości chronometrażu dla każdego testu, transakcji i strony, które zostały uruchomione lub wystawione podczas testu obciążenia w **magazynie wyników testu obciążenia**. Jest to wymagane, jeśli zamierzasz użyć **wykresu aktywności użytkownika wirtualnego** w **analizatorze testu obciążenia**.<br />     Aby uzyskać więcej informacji, zobacz [Analizowanie aktywności użytkownika wirtualnego w widoku Szczegóły](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Brak** — nie należy zbierać żadnych indywidualnych wartości czasu. Jest to wartość domyślna dla programu Visual Studio 2013 Update 4 i nowszych wersji.<br />-   **StatisticsOnly** — zbieraj i przechowuj tylko statystyki zamiast przechowywania indywidualnych wartości chronometrażu dla każdego testu, transakcji i strony, które zostały wykonane lub wydane podczas testu obciążenia w **magazynie wyników testów obciążenia.**<br /><br /> Aby uzyskać więcej informacji, zobacz [Jak: Określanie właściwości magazynu szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>Właściwości śledzenia SQL

|Właściwość|Definicja|
|-|----------------|
|**Minimalny czas trwania śledzonych operacji SQL**|Minimalny czas trwania operacji SQL, które mają być przechwytywane przez śledzenia SQL, w milisekundach. Na przykład to pozwala zignorować operacje, które kończą się szybko, jeśli próbujesz znaleźć operacje SQL, które są powolne pod obciążeniem.|
|**Ciąg połączenia śledzenia SQL**|Parametry połączenia, który jest używany do uzyskiwania dostępu do bazy danych, które mają być śledzone.|
|**Katalog śledzenia SQL**|Lokalizacja, w której plik śledzenia SQL jest umieszczany po zakończeniu śledzenia. Ten katalog musi mieć uprawnienia do zapisu dla programu SQL Server i uprawnienia do odczytu dla kontrolera.|
|**Włączono śledzenie SQL**|Umożliwia to śledzenie operacji SQL. Wartością domyślną jest `False`.|

## <a name="test-iterations-properties"></a>Właściwości iteracji testowych

|Właściwość|Definicja|
|-|----------------|
|**Iteracje testowe**|Określa całkowitą liczbę poszczególnych testów do uruchomienia przed zakończeniem testu obciążenia. Ta właściwość ma zastosowanie tylko wtedy, gdy `True`właściwość "Użyj iteracji testowych" jest.|
|**Użyj iteracji testowych**|Jeśli użyj iteracji `True`testu jest, a następnie test obciążenia jest uruchamiany, dopóki liczba poszczególnych testów ukończonych w teście obciążenia osiągnie liczbę określoną przez "Iteracje testowe" właściwość. W takim przypadku ustawienia oparte na czasie, które są rozgrzewa czas trwania, Czas trwania uruchamiania i Czas trwania schładzania, są ignorowane. Jeśli "Użyj iteracji `False`testowych" jest , wszystkie ustawienia chronometrażu mają zastosowanie, a "Iteracje testowe" jest ignorowany.|

Aby uzyskać więcej informacji, zobacz [Jak: Określanie liczby iteracji testowych w ustawieniu uruchamiania](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Właściwości chronometrażu

|Właściwość|Definicja|
|-|----------------|
|**Czas trwania schładzać**|Czas trwania okresu schładzanego badania, wyrażony w formacie hh:mm:ss. Poszczególne testy w ramach testu obciążenia mogą być nadal uruchomione po zakończeniu testu obciążenia. W okresie schładzać badania te mogą być kontynuowane do czasu ich zakończenia lub zakończenia okresu schładzanego. Domyślnie nie ma okresu schładzania, a poszczególne testy są kończone po zakończeniu testu obciążenia na podstawie ustawienia Czas trwania uruchomienia.|
|**Czas trwania biegu**|Długość testu w formacie hh:mm:ss.|
|**Częstotliwość próbkowania**|Interwał, w którym mają być przechwytywały wartości licznika wydajności w formacie hh:mm:ss.<br /><br /> Aby uzyskać więcej informacji, zobacz [Jak: Określanie częstotliwości próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Czas trwania rozgrzewki**|Okres między rozpoczęciem badania a rozpoczęciem rejestrowania próbek danych w formacie hh:mm:ss. Jest to często używane do krok ładowania użytkowników wirtualnych, aby osiągnąć określony poziom obciążenia przed nagraniem wartości próbki. Przykładowe wartości, które są przechwytywane przed zakończeniem okresu rozgrzewania, są wyświetlane w **analizatorze testu obciążenia**.|

## <a name="webtest-connections-properties"></a>Właściwości połączeń WebTest

|Właściwość|Definicja|
|-|----------------|
|**Model połączenia testu sieci Web**|Służy to do sterowania wykorzystaniem połączeń z agenta testu obciążenia do serwera sieci web dla testów wydajności sieci web, które są uruchamiane wewnątrz testu obciążenia. Dostępne są trzy opcje modelu połączenia testu wydajności sieci Web:<br /><br /> - Model **Połączenia na użytkownika** symuluje zachowanie użytkownika, który korzysta z prawdziwej przeglądarki. Podczas symulowania programu Internet Explorer 6 lub Internet Explorer 7 każdy użytkownik wirtualny, który jest uruchomiony test wydajności sieci Web używa jednego lub dwóch dedykowanych połączeń z serwerem sieci web. Pierwsze połączenie jest ustanawiane po wydaniu pierwszego żądania w teście wydajności sieci web. Drugie połączenie może być używane, gdy strona zawiera więcej niż jedno żądanie zależne. Te żądania są wystawiane równolegle przy użyciu dwóch połączeń. Te połączenia są ponownie używane dla kolejnych żądań w teście wydajności sieci web. Połączenia są zamykane po zakończeniu testu wydajności sieci Web. Wadą tego modelu jest to, że liczba połączeń, które są otwarte na komputerze agenta może być wysoka (do dwóch razy obciążenia użytkownika). W związku z tym zasoby, które są wymagane do obsługi tej liczby połączeń o wysokiej może ograniczyć obciążenie użytkownika, które mogą być napędzane z jednego agenta testu obciążenia. Gdy program Internet Explorer 8 jest symulowany, obsługiwanych jest sześć równoczesnych połączeń.<br />- Model **puli połączeń** oszczędza zasoby agenta testu obciążenia, udostępniając połączenia z serwerem sieci web wśród wielu użytkowników testu wydajności sieci wirtualnej. Jeśli obciążenie użytkownika jest większy niż rozmiar puli połączeń, testy wydajności sieci web, które są uruchamiane przez różnych użytkowników wirtualnych będzie współużytkować połączenie. Może to oznaczać, że jeden test wydajności sieci web może czekać, zanim wyda żądanie, gdy inny test wydajności sieci web używa połączenia. Średni czas oczekiwania testu wydajności sieci web przed przesłaniem żądania jest śledzony przez licznik wydajności testu obciążenia Średni czas oczekiwania na połączenie. Liczba ta powinna być mniejsza niż średni czas odpowiedzi dla strony. Jeśli tak nie jest, rozmiar puli połączeń jest prawdopodobnie zbyt mały.<br />- **Model iteracji połączenia na test** określa użycie dedykowanych połączeń dla każdej iteracji testowej.|
|**Rozmiar puli połączeń webtest**|Określa maksymalną liczbę połączeń między agentem testu obciążenia a serwerem sieci Web. Dotyczy to tylko modelu **puli połączeń.**|

## <a name="change-run-setting-properties"></a>Zmienianie właściwości ustawień przebiegu

Do testu obciążeniowego można dodać więcej parametrów uruchomieniowych z różnymi ustawieniami właściwości, co pozwoli wykonywać te testy w różnych warunkach. Na przykład można dodać nowe ustawienie testu określające inną częstotliwość próbkowania albo dłuższy czas trwania. Można użyć tylko jednego ustawienia uruchamiania naraz i należy określić, które ustawienie uruchamiania do użycia, oznaczając je jako aktywne. Na przykład zobacz [Jak: Wybierz ustawienie aktywnego uruchomienia dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

Aby zmienić ustawienia uruchamiania:

1. Otwórz test obciążenia.

2. Rozwiń folder **Uruchom ustawienia.**

3. Wybierz węzeł **Uruchom ustawienia.**

4. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Zostanie wyświetlone **okno Właściwości** i zostaną wyświetlone właściwości wybranego ustawienia przebiegu.

5. Okno **Właściwości** służy do zmiany ustawień uruchamiania. Na przykład zmień czas trwania uruchomienia na **00:05:00,** aby uruchomić test przez pięć minut.

    > [!NOTE]
    > Aby uzyskać pełną listę właściwości ustawień uruchamiania i ich opisy, zobacz [Właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

6. Po zakończeniu zmiany właściwości, zapisz test obciążenia. W menu **Plik** wybierz polecenie **Zapisz**.

> [!NOTE]
> Mapowania zestawów liczników są również częścią ustawień uruchamiania. Aby uzyskać więcej informacji, zobacz [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
