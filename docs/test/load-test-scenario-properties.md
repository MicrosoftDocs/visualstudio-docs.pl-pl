---
title: Właściwości scenariusza testów obciążenia
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2011438f1fcb0230cde0de527216456553e7c64
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584442"
---
# <a name="load-test-scenario-properties"></a>Właściwości scenariusza testu obciążenia

Zmień ustawienia właściwości scenariusz testu obciążenia w programie Visual Studio, aby spełnić wymagania dotyczące testowania obciążenia. W tym artykule wymieniono różne właściwości scenariusza testu obciążenia według kategorii.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Ogólne

|Właściwość|Definicja|
|-|----------------|
|**Nazwa**|Nazwa scenariusza.|

## <a name="mix"></a>Miks

|Właściwość|Definicja|
|-|----------------|
|**Kombinacja przeglądarki**|Określa kombinację przeglądarki sieci Web dla testu obciążenia. Można określić różne typy przeglądarek internetowych i ich rozkład obciążenia.<br /><br />Wybierz przycisk wielokropek **(...)** , aby otworzyć okno dialogowe **Edytuj miks przeglądarki,** a następnie użyj **opcji Dodaj** i **usuń,** aby wybrać typy przeglądarek internetowych w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, zobacz [Określanie typów przeglądarek internetowych](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Połączenie sieciowe**|Określa mieszany profil sieciowy dla testu obciążeniowego. Można określić, które typy sieci mają zostać objęte testem, oraz rozkład obciążenia między nimi.<br /><br />Wybierz przycisk wielokropek **(...)** , aby otworzyć okno dialogowe **Edycja koszyka sieciowego,** a następnie użyć opcji **Dodaj** i **usuń,** aby wybrać typy sieci w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Mieszanka testowa**|Określa wydajność sieci Web i kombinację testu jednostkowego dla testu obciążenia. Można określić, które testy mają zostać wykonane, oraz rozkład obciążenia między nimi.<br /><br />Wybierz przycisk wielokropek **(...)** , aby otworzyć okno dialogowe **Edycja miksu testowego,** a następnie użyj **opcji Dodaj** i **usuń,** aby wybrać testy w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, [edytuj kombinację testów dla scenariusza testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Typ mieszanki testowej**|Określa model testu mieszanek dla testu obciążenia.<br /><br />Wybierz przycisk wielokropek **(...)** aby otworzyć okno dialogowe **Edycja miksu testowego,** a następnie użyj listy rozwijanej w obszarze **Test mix model,** aby wybrać model miksu testowego do użycia w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, zobacz [Edytowanie modeli miksu tekstu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Opcje

|Właściwość|Definicja|
|-|----------------|
|**Agenci do użycia**|Określa agentów, których ma używać scenariusz, jeśli test obciążenia jest uruchamiany zdalnie. Na przykład można określić konkretny zestaw agentów, aby zachować spójność podczas analizowania trendów wydajności. Agenci mogą być również rozproszeni geograficznie, tak aby istniała koligacja między skryptami wykonywanymi przez agentów a lokalizacją agentów.<br /><br />Agenci muszą być oddzielone przecinkami, na przykład "**Agent1, Agent2, Agent3**". Niewypełnienie tej właściwości oznacza, że scenariusz powinien wykorzystywać wszystkich dostępnych agentów.<br /><br />Aby uzyskać więcej informacji, zobacz [Jak: Określanie agentów testowych do użycia](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Zastosuj dystrybucję do opóźnienia tempa**|Wartość logiczna, która jest używana do określenia, czy chcesz zastosować typowe opóźnienia dystrybucji w modelu mix testu tempa użytkownika. Ta właściwość ma zastosowanie tylko wtedy, gdy właściwość **Test Mix Type** jest ustawiona na Na podstawie tempa **użytkownika**.<br /><br />Aby uzyskać więcej informacji, zobacz [Jak: Stosowanie dystrybucji do opóźnienia tempa](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**Przełączanie IP**|Wartość logiczna używana do określania, czy używane jest przełączanie adresów IP.<br /><br />Przełączanie adresów IP umożliwia agentowi testnemu wysyłanie żądań do serwera przy użyciu zakresu różnych adresów IP. Symuluje wywołania pochodzące z różnych komputerów klienckich. Przełączanie adresów IP jest ważne podczas testowania na farmie internetowej z równoważeniem obciążenia. Większość modułów równoważenia obciążenia ustanawia koligacji między klientem a określonym serwerem sieci web przy użyciu adresu IP klienta. Jeśli wszystkie żądania wydają się pochodzić z jednego klienta, moduł równoważenia obciążenia nie zrównoważy obciążenia. Aby uzyskać dobre równoważenie obciążenia w farmie sieci web, ważne jest, aby żądania pochodzić z zakresu adresów IP.<br /><br />Funkcja przełączania adresów IP jest dostępna w przypadku używania agenta testowego.|
|**Maksymalna iteracje testowe**|Wartość liczbowa służąca do określenia maksymalnej liczby testów, jakie mają zostać wykonane w scenariuszu. Wartość 0 oznacza brak maksimum.<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie iteracji testowych dla scenariuszy](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Odsetek nowych użytkowników**|Wartość liczbowa określająca procent nowych użytkowników lub gości w scenariuszu.<br /><br />Aby uzyskać więcej informacji, zobacz [Jak: Określanie odsetka użytkowników wirtualnych korzystających z danych pamięci podręcznej sieci Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Pomyśl profil**|Określa, czy w scenariuszu będzie używany **rozkład normalny**, czy profil myśli jest **włączony** lub **wyłączony**.<br /><br />Aby uzyskać więcej informacji, zobacz Edytowanie czasów myślenia w [celu symulacji opóźnień interakcji z człowiekiem w witrynie](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Chronometraż

|Właściwość|Definicja|
|-|----------------|
|**Opóźnij czas rozpoczęcia**|Wartość czasu, która wskazuje, ile godzin, minut i sekund ma trwać opóźnienie rozpoczęcia scenariusza po rozpoczęciu testu obciążeniowego. Jeśli właściwość **Disable During Warmup** jest ustawiona na **True**, czas oczekiwania ma zastosowanie po zakończeniu okresu rozgrzewania.<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień uruchamiania scenariusza](../test/configure-scenario-start-delays.md).|
|**Wyłącz podczas rozgrzewki**|Wartość logiczna, która jest używana do określenia, czy scenariusz powinien być uruchamiany, czy nie podczas wartości czasu trwania **rozgrzewania** określonej w ustawieniu uruchomienia testu obciążenia.<br /><br />Aby uzyskać więcej informacji na temat właściwości ustawienia przebiegu testu obciążenia, zobacz [Właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień uruchamiania scenariusza](../test/configure-scenario-start-delays.md).|
|**Czasy między iteracjami testowym**|Wartość liczbowa służąca do określenia czasu oczekiwania (w sekundach) między iteracjami testu.<br /><br />Aby uzyskać więcej informacji, zobacz Edytowanie czasów myślenia w [celu symulacji opóźnień interakcji z człowiekiem w witrynie](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
