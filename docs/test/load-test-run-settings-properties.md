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
ms.prod: visual-studio-dev15
ms.openlocfilehash: 0ab64f1d59e5a183355f665dd720b02a46be98e9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970178"
---
# <a name="load-test-run-settings-properties"></a>Właściwości ustawień przebiegu testu obciążeniowego

Parametry uruchomieniowe testu obciążeniowego decydują o różnych innych ustawień, takich jak czas trwania testu, poziomu szczegółowości zbierania wyników oraz zbiorów liczników, które są zbierane podczas przebiegów testowych. Dla każdego testu obciążeniowego można utworzyć i zapisać wiele parametrów uruchomieniowych, a następnie wybrać jedno konkretne ustawienie do użycia podczas wykonywania testu. Początkowy parametr uruchomieniowy dodaje się do testu obciążeniowego podczas tworzenia test obciążenia przy użyciu **Kreatora nowego testu obciążeniowego**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W poniższych tabelach opisano różne właściwości ustawień przebiegu testu obciążeniowego. Właściwości te można modyfikować, dopasowując do konkretnych wymagań dotyczących testowania obciążeniowego.

Aby uzyskać więcej informacji, zobacz [parametrów uruchomieniowych testu obciążeniowego Konfiguruj](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Właściwości ogólne

|Właściwość|Definicja|
|-|----------------|
|**Opis**|Opis parametrów uruchomieniowych.|
|**Maksymalny błąd według typu**|Maksymalna liczba błędów na typ do zapisania podczas testu obciążenia.<br /><br /> Można zwiększyć tę liczbę, jeśli trzeba, ale w ten sposób spowoduje również zwiększenie rozmiaru i czasu przetwarzania wyniku testu obciążeniowego.|
|**Raportowanych adresów URL żądania maksymalna**|Maksymalna liczba testów wydajności sieci web unikatowy żądania adresów URL, na którym ma zostać wyniki tego testu obciążeniowego.<br /><br /> Można zwiększyć tę liczbę, jeśli trzeba, ale w ten sposób spowoduje również zwiększenie rozmiaru i czasu przetwarzania wyniku testu obciążeniowego.|
|**Maksymalne naruszenia progowe**|Maksymalna liczba naruszeń progowych do zapisania podczas testu obciążenia.<br /><br /> Można zwiększyć tę liczbę, jeśli trzeba, ale w ten sposób spowoduje również zwiększenie rozmiaru i czasu przetwarzania wyniku testu obciążeniowego.|
|**Uruchom testy jednostkowe w domenie aplikacji**|Wartość logiczna określająca, czy każdego zestawu testów jednostkowych uruchomi się w domenie innej aplikacji, gdy test obciążeniowy zawiera testy jednostkowe. Ustawienie domyślne to True.<br /><br /> Testy jednostkowe nie jest wymagane oddzielne domeny lub app.config pliku aplikacji do poprawnego działania, testy jednostkowe może być szybsze wykonywanie, ustawiając wartość tej właściwości, aby `False`.|
|**Nazwa**|Nazwa ustawienia uruchamiania w postaci, w jakiej pojawia się w **parametrów uruchomieniowych** węźle **edytora testu obciążenia**.|
|**Poziom sprawdzania poprawności**|Definiuje najwyższą reguły sprawdzania poprawności, który zostanie wykonany w teście obciążeniowym. Reguły sprawdzania poprawności są skojarzone z żądania testów wydajności sieci web. Każda reguła sprawdzania poprawności ma poziom skojarzone sprawdzania poprawności: **Wysoka**, **średni**, lub **niski**. Ustawienia uruchamiania testu obciążeniowego określą sprawdzania poprawności, które reguły będą uruchamiane podczas testu wydajności sieci web w teście obciążeniowym. Na przykład, jeśli to ustawienie jest równa **średni**, wszystkie reguły walidacji oznaczone jako **średni**, lub **niski** zostanie uruchomiona.|

## <a name="logging-properties"></a>Właściwości rejestrowania

|Właściwość|Definicja|
|-|----------------|
|**Maksymalne dzienniki testu**|Określa maksymalną liczbę dzienników testu do zapisania podczas testu obciążenia. Jeśli wprowadzono wartość maksymalną liczbę dzienników testu zostanie osiągnięty, test obciążenia spowoduje zatrzymanie zbierania dzienników. W związku z tym dzienniki będą zbierane na początku testu nie zakończenia. Test obciążeniowy będą w dalszym ciągu działać do momentu jego zakończeniu.|
|**Zapisz częstotliwość zapisów w dzienniku dla ukończonych testów**|Określa częstotliwość, z jaką będą zapisywane w dzienniku testu. Liczba wskazuje, że jeden z każdym podanej liczby testów zostaną zapisane w dzienniku testu. Na przykład wprowadzenie wartości dziesięciu Określa, że dziesiątym dniu, dwadzieścia, trzydziestą i tak dalej będą zapisywane w dzienniku testu. Ustawienie wartości 0 określa, czy żadnych dzienników testu zostaną zapisane.|
|**Zapisz dziennik podczas niepowodzenia testu**|Wartość logiczna określająca czy gdy zapisywane są dzienniki testów, jeśli test zakończy się niepowodzeniem w teście obciążeniowym. Wartość domyślna to `True`.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Określ, czy niepowodzenia testu są zapisywane do testowania dzienników](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

 Aby uzyskać więcej informacji, zobacz [ustawień rejestrowania testu obciążeniowego Modyfikuj](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Właściwości wyników

|Właściwość|Definicja|
|-|----------------|
|**Typ magazynu**|Sposób przechowywania liczników wydajności, które są uzyskiwane w teście obciążeniowym. Dostępne są następujące opcje:<br /><br /> -   **Baza danych** -wymaga bazy danych SQL, który ma **Store wyników testu obciążenia**.<br />-   **Brak**.|
|**Przechowywanie informacji**|Służy do określenia, który zawiera szczegółowe informacje będą przechowywane w **Store wyników testu obciążenia**. Dostępne są trzy wartości:<br /><br /> -   **AllIndividualDetails** — zbierania i przechowywania wartości poszczególnych chronometraży dla każdego testu, transakcji i strony, które zostało uruchamiania lub wygenerowane podczas badania obciążenia w **Store wyników testu obciążenia**. Jest to wymagane, jeśli zamierzasz używać **wykres aktywności wirtualnych użytkowników** w **analizatora testu obciążenia**.<br />     Aby uzyskać więcej informacji, zobacz [analizować aktywność wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Brak** — nie zbierają żadnych wartości poszczególnych chronometraży. Jest to wartość domyślna dla programu Visual Studio 2013 Update 4 i nowszych wersjach.<br />-   **StatisticsOnly** — zbierania i przechowywania statystyk zamiast przechowywania wartości poszczególnych chronometraży dla każdego testu, transakcji i strony, który został wykonany lub wygenerowane podczas badania obciążenia w **Store wyników testu obciążenia**.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>Właściwości śledzenia SQL

|Właściwość|Definicja|
|-|----------------|
|**Minimalny czas trwania operacji śledzenia SQL**|Minimalny czas trwania operacji SQL to przechwytywać według śledzenia SQL, w milisekundach. Na przykład dzięki temu można zignorować operacji, które szybko wykonać, jeśli próbujesz odnaleźć operacji SQL, które odbywają się wolno w warunkach obciążenia.|
|**Ciąg połączenia śledzenia SQL**|Parametry połączenia, która umożliwia dostęp do bazy danych do śledzenia.|
|**Katalog śledzenia SQL**|Lokalizacja, w którym plik śledzenia SQL jest umieszczany po zakończeniu śledzenia. Ten katalog musi mieć uprawnienia do zapisu dla programu SQL Server i uprawnienia do odczytu dla kontrolera.|
|**Śledzenie SQL jest włączone**|Umożliwia to śledzenie operacji SQL. Wartość domyślna to `False`.|

## <a name="test-iterations-properties"></a>Właściwości iteracji testu

|Właściwość|Definicja|
|-|----------------|
|**Iteracje testu**|Określa, całkowita liczba testów do uruchomienia przed zakończeniem testu obciążeniowego. Ta właściwość jest stosowana tylko w przypadku właściwości "Użyj iteracji testu" `True`.|
|**Użyj iteracji testu**|W przypadku użycia iteracje testu `True`, a następnie uruchamia test obciążeniowy, dopóki nie osiągnie liczbę indywidualnych testów zakończył w obrębie testu obciążeniowego liczba, która jest określona przez właściwość "Iteracje testu". W takim przypadku ustawienia na podstawie czasu, które są Rozgrzewki czasu trwania, czas trwania uruchomienia oraz czas trwania ochładzania, są ignorowane. Jeśli jest "Użyj iteracji testu" `False`, zastosuj wszystkie ustawienia czasu i "Iteracjami testu" zostanie zignorowany.|

 Aby uzyskać więcej informacji, zobacz [jak: Określanie liczby iteracji testowych w ustawieniach testu](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Właściwości czasu

|Właściwość|Definicja|
|-|----------------|
|**Czas trwania ochładzania**|Czas trwania okresu ochładzania testu, wyrażone w formacie: mm: ss. Po zakończeniu testu obciążenia, może być nadal uruchomiony indywidualnych testów w teście obciążeniowym. Podczas okresu ochładzania tych testów można kontynuować do momentu zakończenia lub zostanie osiągnięty koniec okresu ochładzania. Domyślnie jest nie okres ochładzania, a poszczególne testy zostaną zakończone, gdy zakończy się zgodnie z ustawieniem czas trwania uruchomienia testu obciążenia.|
|**Czas trwania przebiegu**|Długość testu, w formacie: mm: ss.|
|**Częstotliwość próbkowania**|Interwał, w którym będą przechwytywane wartości licznika wydajności w formacie: mm: ss.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Rozgrzewanie czas trwania**|Okres między rozpoczęciem badania i kiedy próbek danych rozpoczyna rejestrowane w formacie: mm: ss. Służy to często krok obciążenia wirtualnych użytkowników, osiągnięcie określonego poziomu obciążenia, zanim rejestrowanie wartości przykładowych. Przykładowe wartości, które są przechwytywane przed zakończeniem okresu rozgrzewania są wyświetlane w **analizatora testu obciążenia**.|

## <a name="webtest-connections-properties"></a>Właściwości połączenia WebTest

|Właściwość|Definicja|
|-|----------------|
|**Model połączenia WebTest**|Ta opcja kontroluje użycie połączenia z agent testu obciążeniowego, aby serwer sieci web testów wydajności sieci web działających w teście obciążeniowym. Dostępne są trzy opcje model połączenia testu sieci web wydajności:<br /><br /> **Connection Per User** modelu symuluje działanie użytkownika, który używa rzeczywista przeglądarka. Gdy program Internet Explorer 6 lub Internet Explorer 7 jest symulowane, każdy użytkownik wirtualny, który uruchamia test wydajności sieci web używa co najmniej dwa dedykowane połączenia z serwerem sieci web. Pierwsze połączenie zostanie nawiązane, po wygenerowaniu pierwszego żądania w teście wydajności sieci web. Drugie połączenie mogą być używane, gdy strona zawiera więcej niż jedno żądanie zależne. Te żądania są wysyłane równolegle za pomocą dwóch połączeń. Te połączenia są używane do obsługi kolejnych żądań w teście wydajności sieci web. Połączenia zostaną zamknięte po zakończeniu testu wydajności sieci web. Wadą tego modelu jest, że liczba połączeń jest otwarte na komputerze agenta może być wysoki (maksymalnie dwa razy obciążenie użytkownikami). W związku z tym zasoby, które są wymagane do obsługi to liczba połączeń wysokiej może ograniczyć obciążenie użytkownikami, które mogą być napędzane z agenta testu obciążenia. Gdy jest symulowane programu Internet Explorer 8, sześciu równoczesnych połączeń są obsługiwane.<br />**Puli połączeń** modelu oszczędza zasoby na agent testu obciążeniowego za pomocą udostępniania połączenia z serwerem sieci web przez wielu użytkowników testu wydajności sieci web wirtualne. Jeśli obciążenie użytkownikami jest większy niż rozmiar puli połączeń, testy wydajności sieci web, które są uruchamiane przez różnych użytkowników wirtualnych współużytkują połączenia. Może to oznaczać, że ten test wydajności sieci web w jeden może być konieczne poczekanie przed generuje żądanie, korzystając z innego testu wydajności sieci web jest połączenie. Średni czas testu wydajności sieci web czeka przed prześle powiadomienie, że żądania są śledzone przez licznik wydajności testu obciążeniowego Średni czas oczekiwania połączenia. Liczba ta powinna być mniejsza niż średni czas odpowiedzi dla strony. Jeśli nie jest, prawdopodobnie jest za mały rozmiar puli połączeń.<br />**Połączenia na Test iteracji** modelu Określa użycie dedykowanego połączenia dla każdej iteracji testu.|
|**Rozmiar puli połączeń WebTest**|Określa maksymalną liczbę połączeń między agent testu obciążeniowego i serwer sieci Web. Dotyczy to tylko **puli połączeń** modelu.|

##  <a name="change-run-setting-properties"></a>Zmiana właściwości ustawienia przebiegu
 Do testu obciążeniowego można dodać więcej parametrów uruchomieniowych z różnymi ustawieniami właściwości, co pozwoli wykonywać te testy w różnych warunkach. Na przykład można dodać nowe ustawienie testu określające inną częstotliwość próbkowania albo dłuższy czas trwania. Można używać tylko jednego naraz, a następnie należy określić, które uruchomieniowego do użycia, oznaczając je jako aktywny. Aby uzyskać przykład, zobacz [jak: Wybierz aktywne ustawienia uruchamiania dla testu obciążeniowego](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

### <a name="to-change-run-settings"></a>Aby zmienić ustawienia uruchamiania

1.  Otwórz test obciążenia.

2.  Rozwiń **parametrów uruchomieniowych** folderu.

3.  Wybierz **parametrów uruchomieniowych** węzła.

4.  Na **widoku** menu, wybierz **okno właściwości**.

     **Okno właściwości** jest wyświetlany i wyświetlane są właściwości dla wybranego parametru uruchomieniowego.

5.  Użyj **okno właściwości** do zmiany parametrów uruchomieniowych. Na przykład zmienić czas trwania testu na **00:05:00** Aby uruchomić test na pięć minut.

    > [!NOTE]
    > Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawienia przebiegu testu obciążeniowego](../test/load-test-run-settings-properties.md).

6.  Po zakończeniu zmiany właściwości, należy zapisać testu obciążenia. Na **pliku** menu, wybierz **Zapisz**.

> [!NOTE]
> Mapowania zestawów liczników są również częścią parametrów uruchomieniowych. Aby uzyskać więcej informacji, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)