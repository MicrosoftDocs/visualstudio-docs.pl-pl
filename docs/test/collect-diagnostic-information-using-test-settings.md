---
title: Zbieranie informacji diagnostycznych przy użyciu ustawień testu
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e853e0ec54179178eba0f1566c34d7cfd63cee5
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880289"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Zbieranie informacji diagnostycznych przy użyciu ustawień testu

Ustawienia *testu* w programie Visual Studio można użyć do zbierania dodatkowych danych po uruchomieniu testów. Na przykład można nagrać wideo podczas uruchamiania testu. Istnieją karty danych diagnostycznych do:

- Zbieranie każdego kroku akcji interfejsu użytkownika w formacie tekstowym

- Nagrywanie każdej akcji interfejsu użytkownika w celu odtworzenia

- Zbieranie informacji o systemie

- Zbieranie danych dziennika zdarzeń

- Zbieranie danych IntelliTrace w celu wyizolowania niezwielanych błędów

Karty danych diagnostycznych mogą być również używane do zmiany zachowania komputera testowego. Na przykład za pomocą ustawienia testu w programie Visual Studio można emulować różne wąskie gardła topologii sieci, aby ocenić wydajność aplikacji zespołu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Używanie ustawień testowych w programie Visual Studio

Aby uruchomić jednostkę, kodowany interfejs użytkownika, wydajność sieci web lub testy obciążenia przy użyciu programu Visual Studio, można dodać, skonfigurować i wybrać ustawienia testu do użycia podczas uruchamiania testów. Aby uruchomić testy, zbierać dane lub wpływać na komputer testowy zdalnie, należy określić kontroler testów do użycia w ustawieniach testu. Kontroler testów ma agentów, które mogą być używane dla każdej roli w ustawieniach testu.

## <a name="diagnostic-data-adapter-details"></a>Szczegóły karty danych diagnostycznych

Poniższa tabela zawiera omówienie różnych sposobów konfigurowania kart danych diagnostycznych do użytku z rolami komputera lokalnego lub zdalnego.

|Karta danych diagnostycznych używana w ustawieniu testowym|Testy ręczne na komputerze lokalnym|Testy automatyczne|Testy ręczne: zbieranie danych przy użyciu zestawu ról i środowiska|Uwagi|
|-|-|-|-|-|
|**ASP.NET serwer proxy klienta dla intellitrace i wpływ testu:** Ten serwer proxy umożliwia zbieranie informacji o wywołaniach http z klienta do serwera sieci web dla kart danych diagnostycznych IntelliTrace i Test Impact.|Tak|Tak|Tak|- Użyj tego tylko wtedy, gdy karty danych diagnostycznych IntelliTrace lub Test Impact są wybrane dla roli klienta.|
|**ASP.NET profiler:** Można utworzyć ustawienie testowe, które obejmuje profilowanie ASP.NET, które zbiera dane o wydajności ASP.NET aplikacji sieci web.|Nie|Tak (patrz uwagi)|Nie|- Ta karta danych diagnostycznych jest obsługiwana tylko po uruchomieniu testów obciążenia z programu Visual Studio.|
|**Pokrycie kodu:** Można utworzyć ustawienie testu, który zawiera informacje o pokryciu kodu, który jest używany do zbadania, jaka część kodu jest objęta testami.|Nie|Tak (patrz uwagi)|Nie|- Pokrycie kodu można używać tylko po uruchomieniu automatycznego testu z programu Visual Studio lub *mstest.exe*i tylko z komputera, który uruchamia test. Kolekcja zdalna nie jest obsługiwana.<br />- Zbieranie danych pokrycia kodu nie działa, jeśli masz również ustawienie testu skonfigurowane do zbierania informacji IntelliTrace. **Uwaga:**  Ta karta danych diagnostycznych ma zastosowanie tylko do ustawień testu programu Visual Studio. Nie jest używany dla ustawień testowych w programie Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). Ponadto ta karta jest dla zgodności z projektami testowymi programu Visual Studio 2010. **Uwaga:**  W celu zapewnienia zgodności pokrycie kodu ma zastosowanie, gdy zautomatyzowane testy są uruchamiane z menedżera testów firmy Microsoft lub zdalnego agenta testowego z programu Visual Studio przy użyciu starszego modułu uruchamiającego MSTest.|
|**Dziennik zdarzeń:** Można skonfigurować ustawienie testu, aby uwzględnić zbieranie dzienników zdarzeń, które jest zawarte w wynikach testu.|Tak|Tak|Tak||
|**IntelliTrace:** Można skonfigurować kartę danych diagnostycznych dla *IntelliTrace* do zbierania określonych informacji śledzenia diagnostycznego, aby ułatwić izolowanie błędów, które są trudne do odtworzenia. Spowoduje to utworzenie pliku IntelliTrace zawierającego te informacje. Plik IntelliTrace ma rozszerzenie *.iTrace*. Gdy test zakończy się niepowodzeniem, można utworzyć błąd. Plik IntelliTrace, który jest zapisywany wraz z wynikami testu, jest automatycznie połączony z tym błędem. Dane, które są zbierane w pliku IntelliTrace zwiększa wydajność debugowania, zmniejszając czas wymagany do odtworzenia i zdiagnozowania błędu w kodzie. Z tego pliku IntelliTrace sesji lokalnej można symulować na innym komputerze. Zmniejsza to ryzyko, że błąd nie jest odtwarzalny.|Tak|Tak|Tak|- Jeśli włączysz zbieranie danych IntelliTrace, zbieranie danych pokrycia kodu nie działa.<br />- Jeśli używasz IntelliTrace dla roli klienta sieci web, należy również wybrać ASP.NET serwera proxy klienta dla intellitrace i test wpływ karty danych diagnostycznych.<br />- Obsługiwane są tylko następujące wersje iis: IIS 7.0, IIS 7.5 i IIS 8.0.|
|**Emulacja sieci:** Można określić, że chcesz umieścić sztuczne obciążenie sieciowe na teście przy użyciu ustawienia testu. Emulacja sieci wpływa na komunikację do i z komputera, emulując określoną szybkość połączenia sieciowego, taką jak dial-up. |Nie|Tak (patrz uwagi)|Nie|Można użyć karty danych diagnostycznych emulacji sieciowej dla roli klienta lub serwera. Nie trzeba używać karty na obu tych ról, które komunikują się ze sobą. **Uwaga:**  Ta karta danych diagnostycznych ma zastosowanie tylko do ustawień testu programu Visual Studio. Nie jest używany dla ustawień testowych w programie Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). **Uwaga:**  Nie można użyć emulacji sieci w celu zwiększenia szybkości połączenia sieciowego. **Ostrzeżenie:**  Jeśli karta danych diagnostycznych emulacji sieciowej zostanie uwzględnina w ustawieniach testowych i zamierzasz jej używać na komputerze lokalnym, należy również powiązać sterownik emulacji sieciowej z jedną z kart sieciowych komputera. Sterownik emulacji sieci jest wymagany do działania karty danych diagnostycznych emulacji sieciowej. Sterownik emulacji sieci jest zainstalowany i powiązany z kartą na dwa sposoby: <ul><li>**Sterownik emulacji sieci zainstalowany z programem Microsoft Visual Studio Test Agent:** Visual Studio Agent testowy może służyć zarówno na komputerach zdalnych i komputera lokalnego. Po zainstalowaniu programu Visual Studio Test Agent, proces instalacji zawiera krok konfiguracji, który wiąże sterownik emulacji sieci do karty sieciowej. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).</li><li>**Sterownik emulacji sieci zainstalowany w programie Microsoft Visual Studio Test Professional:** Podczas korzystania z emulacji sieci po raz pierwszy zostanie wyświetlony monit o powiązanie sterownika emulacji sieci z kartą sieciową.</li></ul> Można również zainstalować sterownik emulacji sieci z wiersza polecenia na komputerze lokalnym bez instalowania agenta testowego programu Visual Studio za pomocą następującego polecenia: **VSTestConfig NETWORKEMULATION /install** **Warning:** Karta emulacji sieci jest ignorowana przez testy obciążenia. Zamiast tego testy obciążenia używają ustawień, które są określone w kombinacji sieciowej scenariusza testu obciążenia.|
|**Informacje o systemie:** Ustawienie testu można skonfigurować w taki sposób, aby zawierało informacje o systemie o komputerze, na którym test jest uruchamiany.|Tak|Tak|Tak||
|**Wpływ testu:** Można zbierać informacje o tym, które metody kodu aplikacji zostały użyte podczas uruchamiania przypadku testowego. Może to być używane wraz ze zmianami w kodzie aplikacji, który został wprowadzony przez deweloperów, aby określić, które testy zostały naruszone przez te zmiany rozwoju.|Tak|Tak|Tak|- Jeśli zbierasz dane wpływu testu dla roli klienta sieci web, należy również wybrać ASP.NET serwera proxy klienta dla karty danych diagnostycznych IntelliTrace i Test Impact.<br />- Obsługiwane są tylko następujące wersje iis: IIS 7.0, IIS 7.5 i IIS 8.0.|
|**Rejestrator wideo:** Po uruchomieniu testu można utworzyć nagranie wideo sesji pulpitu. Film może pomóc innym członkom zespołu izolować problemy z aplikacjami, które są trudne do odtworzenia.|Tak|Tak (patrz uwagi)|Tak|- Jeśli włączysz oprogramowanie agenta testowego do uruchomienia jako proces zamiast usługi, można utworzyć nagranie wideo po uruchomieniu automatycznych testów.|
