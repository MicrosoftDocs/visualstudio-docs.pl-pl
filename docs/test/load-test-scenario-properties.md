---
title: Właściwości scenariusza testów obciążenia
description: Dowiedz się, jak zmienić ustawienia właściwości scenariusza testu obciążenia w programie Visual Studio na jedną z różnych właściwości scenariusza testu obciążenia w tym artykule.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 36c93d11e64b01820a3a31c73beccadb24ffa08c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887669"
---
# <a name="load-test-scenario-properties"></a>Właściwości scenariusza testu obciążenia

Zmień ustawienia właściwości scenariusza testu obciążenia w programie Visual Studio, aby spełnić wymagania dotyczące testowania obciążenia. W tym artykule wymieniono różne właściwości scenariusza testu obciążenia według kategorii.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Ogólne

|Właściwość|Definicja|
|-|----------------|
|**Nazwa**|Nazwa scenariusza.|

## <a name="mix"></a>Miks

|Właściwość|Definicja|
|-|----------------|
|**Mieszanie przeglądarki**|Określa mieszanie przeglądarki sieci Web w teście obciążenia. Można określić różne typy przeglądarek sieci Web i ich rozkład obciążenia.<br /><br />Wybierz przycisk wielokropka **(...)** , aby otworzyć okno dialogowe **Edytowanie mieszanki przeglądarki** , a następnie użyj opcji **Dodaj** i **Usuń** , aby wybrać typy przeglądarek sieci Web w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, zobacz [Określanie typów przeglądarek sieci Web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Mieszanie sieci**|Określa mieszany profil sieciowy dla testu obciążeniowego. Można określić, które typy sieci mają zostać objęte testem, oraz rozkład obciążenia między nimi.<br /><br />Wybierz przycisk wielokropka **(...)** , aby otworzyć okno dialogowe **Edytuj miks sieciowy** i użyć opcji **Dodaj** i **Usuń** , aby wybrać typy sieci w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Test mieszany**|Określa mieszany test wydajności sieci Web i testów jednostkowych dla testu obciążenia. Można określić, które testy mają zostać wykonane, oraz rozkład obciążenia między nimi.<br /><br />Wybierz przycisk wielokropka **(...)** , aby otworzyć okno dialogowe **Edytuj test mieszany** , a następnie użyj polecenia **Dodaj** i **Usuń** , aby wybrać testy w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, [Edytuj mieszany test dla scenariusza testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Typ testu mieszanego**|Określa model testu mieszanego dla testu obciążenia.<br /><br />Wybierz przycisk wielokropka **(...)** , aby otworzyć okno dialogowe **Edytuj test mieszany** , a następnie użyj listy rozwijanej w obszarze **model testu mieszanego** , aby wybrać model testu mieszanego do użycia w teście obciążenia.<br /><br />Aby uzyskać więcej informacji, zobacz [Edit Text mix models](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Opcje

|Właściwość|Definicja|
|-|----------------|
|**Agenci do użycia**|Określa agentów, których scenariusz ma używać w przypadku zdalnego uruchamiania testu obciążenia. Na przykład można określić konkretny zestaw agentów, aby zachować spójność podczas analizowania trendów wydajności. Agenci mogą być również rozproszeni geograficznie, tak aby istniała koligacja między skryptami wykonywanymi przez agentów a lokalizacją agentów.<br /><br />Agenci muszą być oddzielone przecinkami, na przykład "**agenta 1, agenta 2, agenta 3**". Niewypełnienie tej właściwości oznacza, że scenariusz powinien wykorzystywać wszystkich dostępnych agentów.<br /><br />Aby uzyskać więcej informacji, zobacz [How to: Określ agentów testowych do użycia](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Zastosuj rozkład do opóźnienia tempem**|Wartość logiczna, która jest używana do określenia, czy chcesz zastosować typowe opóźnienia dystrybucji w modelu mieszanym testu tempem użytkownika. Ta właściwość ma zastosowanie tylko wtedy, gdy właściwość **test mix Type** ma ustawioną wartość na **podstawie tempa użytkownika**.<br /><br />Aby uzyskać więcej informacji, zobacz [jak: stosowanie dystrybucji do opóźnienia tempem](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**Przełączanie adresów IP**|Wartość logiczna, która jest używana do określenia, czy jest używane Przełączanie adresów IP.<br /><br />Przełączenie IP pozwala agentowi testowemu wysyłać żądania do serwera przy użyciu różnych adresów IP. Symuluje to wywołania pochodzące z różnych komputerów klienckich. Przełączanie IP jest ważne w przypadku testowania względem kolektywu serwerów sieci Web z równoważeniem obciążenia. Większość modułów równoważenia obciążenia ustanawia koligację między klientem a określonym serwerem sieci Web przy użyciu adresu IP klienta. Jeśli wszystkie żądania wyglądają jak pochodzą z jednego klienta, moduł równoważenia obciążenia nie będzie zrównoważyć obciążenia. Aby uzyskać dobre Równoważenie obciążenia w kolektywie serwerów sieci Web, należy pamiętać, że żądania pochodzą z zakresu adresów IP.<br /><br />Funkcja przełączania adresów IP jest dostępna w przypadku używania agenta testowego.|
|**Maksymalna liczba iteracji testu**|Wartość liczbowa służąca do określenia maksymalnej liczby testów, jakie mają zostać wykonane w scenariuszu. Wartość 0 oznacza brak maksimum.<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie iteracji testowych dla scenariuszy](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Procent nowych użytkowników**|Wartość liczbowa określająca procent nowych użytkowników lub gości w scenariuszu.<br /><br />Aby uzyskać więcej informacji, zobacz [How to: Określanie procentu użytkowników wirtualnych korzystających z danych w pamięci podręcznej sieci Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Profil myśli**|Określa, czy scenariusz będzie używać **rozkładu normalnego**, czy też profil myśli jest **włączony** czy **wyłączony**.<br /><br />Aby uzyskać więcej informacji, zobacz [Edytowanie czasów reakcji w celu symulowania opóźnień interakcji z witryną sieci Web](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Chronometraż

|Właściwość|Definicja|
|-|----------------|
|**Opóźnienie godziny rozpoczęcia**|Wartość czasu, która wskazuje, ile godzin, minut i sekund ma trwać opóźnienie rozpoczęcia scenariusza po rozpoczęciu testu obciążeniowego. Jeśli właściwość **disable podczas rozgrzewania** ma wartość **true**, czas oczekiwania będzie obowiązywać po zakończeniu okresu rozgrzewania.<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień uruchamiania scenariusza](../test/configure-scenario-start-delays.md).|
|**Wyłącz podczas rozgrzewania**|Wartość logiczna, która jest używana do określenia, czy scenariusz ma być uruchamiany, czy nie w wartości czasu właściwości czas **trwania rozgrzewania** określonej w ustawieniu przebiegu testu obciążenia.<br /><br />Aby uzyskać więcej informacji na temat właściwości ustawienia przebiegu testu obciążenia, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień uruchamiania scenariusza](../test/configure-scenario-start-delays.md).|
|**Czasy reakcji między iteracjami testu**|Wartość liczbowa służąca do określenia czasu oczekiwania (w sekundach) między iteracjami testu.<br /><br />Aby uzyskać więcej informacji, zobacz [Edytowanie czasów reakcji w celu symulowania opóźnień interakcji z witryną sieci Web](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
