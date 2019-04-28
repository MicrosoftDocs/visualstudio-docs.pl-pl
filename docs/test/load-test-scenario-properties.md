---
title: Właściwości scenariusza testów obciążenia
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86ed8346a27a02eb7e04c1f7a9fa361b0e03431a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62785959"
---
# <a name="load-test-scenario-properties"></a>Właściwości scenariusza testów obciążenia

Zmienić ustawienia właściwości scenariusza testu obciążenia w programie Visual Studio w celu spełnienia wymagań dotyczących testowania obciążenia. W tym artykule wymieniono różne właściwości scenariusza testów obciążenia według kategorii.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Ogólne

|Właściwość|Definicja|
|-|----------------|
|**Nazwa**|Nazwa scenariusza.|

## <a name="mix"></a>Miks

|Właściwość|Definicja|
|-|----------------|
|**Browser Mix**|Określa Miks przeglądarki internetowej dla testu obciążeniowego. Można określić typy przeglądarki innej witryny sieci web oraz rozkład obciążenia między nimi.<br /><br />Wybierz przycisk wielokropka **(...)**  przycisk, aby otworzyć **Edytuj mieszaną przeglądarkę** okno i użyj **Dodaj** i **Usuń** wybrać typy przeglądarek sieci web w teście obciążeniowym.<br /><br />Aby uzyskać więcej informacji, zobacz [Określanie typów przeglądarek sieci web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Mieszany profil sieciowy**|Określa mieszany profil sieciowy dla testu obciążeniowego. Można określić, które typy sieci mają zostać objęte testem, oraz rozkład obciążenia między nimi.<br /><br />Wybierz przycisk wielokropka **(...)**  przycisk, aby otworzyć **Edytuj mieszany profil sieciowy** okno dialogowe i użyj **Dodaj** i **Usuń** wybierz typy sieci do testu obciążeniowego.<br /><br />Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Test Mix**|Określa, że wydajność sieci web oraz testów jednostkowych mieszanego dla testu obciążeniowego. Można określić, które testy mają zostać wykonane, oraz rozkład obciążenia między nimi.<br /><br />Wybierz przycisk wielokropka **(...)**  przycisk, aby otworzyć **Edytuj Test mieszany** okno dialogowe i użyj **Dodaj** i **Usuń** do wybierania testów w teście obciążeniowym.<br /><br />Aby uzyskać więcej informacji [Edytuj test mieszany w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Typ testu mieszanego**|Określa model testu mieszanego dla testu obciążeniowego.<br /><br />Wybierz przycisk wielokropka **(...)**  przycisk, aby otworzyć **Edytuj Test mieszany** okno dialogowe i użyj listy rozwijanej w obszarze **model testu mieszanego** można wybrać model mieszaniny testu do użycia w teście obciążeniowym.<br /><br />Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Opcje

|Właściwość|Definicja|
|-|----------------|
|**Agenci do użycia**|Określa, że agenci, którzy mają używać, jeśli uruchamiasz obciążenie dany Scenariusz testów zdalnie. Na przykład można określić konkretny zestaw agentów, aby zachować spójność podczas analizowania trendów wydajności. Agenci mogą być również rozproszeni geograficznie, tak aby istniała koligacja między skryptami wykonywanymi przez agentów a lokalizacją agentów.<br /><br />Agenci muszą być rozdzielone przecinkami, na przykład "**agenta agenta 1, agenta 2, 3**". Niewypełnienie tej właściwości oznacza, że scenariusz powinien wykorzystywać wszystkich dostępnych agentów.<br /><br />Aby uzyskać więcej informacji, zobacz [jak: Określanie agentów testowych do użycia](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Zastosuj rozkład do opóźnienia do**|Wartość logiczna, która służy do określania, czy chcesz stosowane typowe rozkłady opóźnienia model testu mieszanego z tempem użytkownika. Ta właściwość ma zastosowanie tylko, jeśli **typ testu mieszanego** właściwość jest ustawiona na **oparty na tempie użytkownika**.<br /><br />Aby uzyskać więcej informacji, zobacz [jak: Zastosuj rozkład do opóźnienia do](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**Przełączanie adresów IP**|Wartość logiczna, która służy do określania, jeśli używane jest przełączanie IP.<br /><br />Przełączanie IP pozwala agentowi testowemu wysyłać żądania do serwera przy użyciu szeregu różnych adresów IP. Symuluje to wywołania, które pochodzą z różnych komputerów klienckich. Przełączanie IP jest ważne w przypadku, gdy testujemy obciążenia o zrównoważonym obciążeniu farmy sieci web. Większość usług równoważenia obciążenia ustanawia koligację między klientem i serwerem namierzenie internetowego przy użyciu adresu IP klienta. Jeśli wszystkie żądania wydają się przychodzić od jednego klienta, moduł równoważenia obciążenia nie zrównoważy obciążenia. Aby uzyskać równowagę obciążenia w kolektywie serwerów sieci web, jest ważne, że żądania pochodzą z zakresu adresów IP.<br /><br />Funkcja przełączania adresów IP jest dostępna w przypadku używania agenta testowego.|
|**Maksymalna liczba iteracji testu**|Wartość liczbowa służąca do określenia maksymalnej liczby testów, jakie mają zostać wykonane w scenariuszu. Wartość 0 oznacza brak maksimum.<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie iteracji testowych dla scenariuszy](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Procent nowych użytkowników**|Wartość liczbowa określająca procent nowych użytkowników lub gości w scenariuszu.<br /><br />Aby uzyskać więcej informacji, zobacz [jak: Określ wartość procentową użytkowników wirtualnych korzystających z danych w pamięci podręcznej sieci web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Profil reakcji**|Określa, czy scenariusz będzie używać **rozkładu normalnego**, czy profil reakcji **na** lub **poza**.<br /><br />Aby uzyskać więcej informacji, zobacz [reakcji edycji razy do symulacji witryny sieci Web symulujący opóźnienia wynikające z](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Chronometraż

|Właściwość|Definicja|
|-|----------------|
|**Opóźnienie czasu rozpoczęcia**|Wartość czasu, która wskazuje, ile godzin, minut i sekund ma trwać opóźnienie rozpoczęcia scenariusza po rozpoczęciu testu obciążeniowego. Jeśli **Wyłącz podczas rozgrzewania** właściwość jest ustawiona na **True**, czas oczekiwania stosuje się po zakończeniu okresu rozgrzewania.<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień uruchamiania scenariuszy](../test/configure-scenario-start-delays.md).|
|**Wyłącz podczas rozgrzewania**|Wartość logiczna, która służy do określania, czy powinno być ono uruchomione tego scenariusza nie podczas **czas trwania rozgrzewania** ustawieniu przebiegu wartość czasu właściwości określone w teście obciążeniowym.<br /><br />Aby uzyskać więcej informacji dotyczących właściwości ustawienia przebiegu testu obciążenia, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień uruchamiania scenariuszy](../test/configure-scenario-start-delays.md).|
|**Czasy reakcji pomiędzy iteracjami testu**|Wartość liczbowa służąca do określenia czasu oczekiwania (w sekundach) między iteracjami testu.<br /><br />Aby uzyskać więcej informacji, zobacz [reakcji edycji razy do symulacji witryny sieci Web symulujący opóźnienia wynikające z](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)