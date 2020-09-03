---
title: Zbieranie informacji diagnostycznych za pomocą ustawień testu
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14d98e34ef35efb1498d37071b2f53ef25bac4ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288861"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Zbieranie informacji diagnostycznych za pomocą ustawień testu

Za pomocą *ustawień testu* w programie Visual Studio można zbierać dodatkowe dane podczas uruchamiania testów. Na przykład możesz chcieć nagrać wideo podczas wykonywania testu. Istnieją karty danych diagnostycznych do:

- Zbieraj każdy krok akcji interfejsu użytkownika w formacie tekstowym

- Rejestruj każdą akcję interfejsu użytkownika do odtwarzania

- Zbierz informacje o systemie

- Zbieranie danych dziennika zdarzeń

- Zbieraj dane IntelliTrace, aby ułatwić odizolowanie błędów nieodtwarzalnych

Adaptery danych diagnostycznych mogą również służyć do zmiany zachowania maszyny testowej. Na przykład przy użyciu ustawienia testu w programie Visual Studio można emulować różne wąskie gardła topologii sieci w celu oceny wydajności aplikacji zespołu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Używanie ustawień testu w programie Visual Studio

Aby uruchomić jednostkę, kodowanego interfejsu użytkownika, wydajności sieci Web lub testów obciążenia za pomocą programu Visual Studio, można dodać, skonfigurować i wybrać ustawienia testu, które będą używane podczas uruchamiania testów. Aby uruchomić testy, zebrać dane lub wpływać na maszynę testową zdalnie, należy określić kontroler testów do użycia w ustawieniach testu. Kontroler testów ma agentów, których można użyć dla każdej roli w ustawieniach testu.

## <a name="diagnostic-data-adapter-details"></a>Szczegóły adaptera danych diagnostycznych

Poniższa tabela zawiera omówienie różnych sposobów konfigurowania adapterów danych diagnostycznych do użytku z rolami maszyn lokalnych lub zdalnych.

|Adapter danych diagnostycznych, który jest używany w ustawieniu testu|Testy ręczne na komputerze lokalnym|Testy automatyczne|Testy ręczne: zbieranie danych przy użyciu zestawu ról i środowiska|Uwagi|
|-|-|-|-|-|
|**ASP.NET serwer proxy klienta dla IntelliTrace i wpływu na testowanie:** Ten serwer proxy umożliwia zbieranie informacji o wywołaniach http z klienta do serwera sieci Web dla IntelliTrace i adapterów danych diagnostycznych dotyczących wpływu testów.|Tak|Tak|Tak|— Użyj tej opcji tylko wtedy, gdy dla roli klienta wybrano adaptery danych diagnostycznych dotyczące IntelliTrace lub wpływu na testowanie.|
|**Profiler ASP.NET:** Można utworzyć ustawienie testu, które obejmuje profilowanie ASP.NET, które zbiera dane dotyczące wydajności w aplikacjach sieci Web ASP.NET.|Nie|Tak (Zobacz uwagi)|Nie|— Ta karta danych diagnostycznych jest obsługiwana tylko w przypadku uruchamiania testów obciążenia z programu Visual Studio.|
|**Pokrycie kodu:** Można utworzyć ustawienie testu, które zawiera informacje o pokryciu kodu, które są używane do badania, jaka część kodu jest objęta testami.|Nie|Tak (Zobacz uwagi)|Nie|— Można użyć pokrycia kodu tylko podczas uruchamiania testu automatycznego z programu Visual Studio lub *mstest.exe*i tylko z komputera, na którym jest uruchamiany test. Kolekcja zdalna nie jest obsługiwana.<br />-Zbieranie danych pokrycia kodu nie działa, jeśli istnieje również ustawienie testu skonfigurowane do zbierania informacji IntelliTrace. **Uwaga:**  Ten adapter danych diagnostycznych ma zastosowanie tylko do ustawień testu programu Visual Studio. Nie jest on używany dla ustawień testu w Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). Ponadto ten adapter jest przeznaczony do zgodności z projektami testowymi programu Visual Studio 2010. **Uwaga:**  W celu zapewnienia zgodności, pokrycie kodu jest stosowane, gdy testy automatyczne są uruchamiane z Microsoft Test Manager lub na zdalnym agencie testowym z programu Visual Studio przy użyciu starszego modułu uruchamiającego MSTest.|
|**Dziennik zdarzeń:** Można skonfigurować ustawienie testu, aby uwzględnić zbieranie dzienników zdarzeń, które jest zawarte w wynikach testu.|Tak|Tak|Tak||
|**IntelliTrace:** Adapter danych diagnostycznych dla *IntelliTrace* można skonfigurować do zbierania określonych informacji śledzenia diagnostycznego w celu ułatwienia izolowania błędów, które są trudne do odtworzenia. Spowoduje to utworzenie pliku IntelliTrace, który zawiera te informacje. Plik IntelliTrace ma rozszerzenie *. iTrace*. Gdy test zakończy się niepowodzeniem, można utworzyć usterkę. Plik IntelliTrace, który jest zapisywany wraz z wynikami testu, jest automatycznie połączony z tą usterką. Dane zbierane w pliku IntelliTrace zwiększają produktywność debugowania, skracając czas wymagany do odtworzenia i zdiagnozowania błędu w kodzie. Z tego pliku IntelliTrace sesja lokalna może być symulowana na innym komputerze. Zmniejsza to ryzyko wystąpienia błędu niepowtarzającego się.|Tak|Tak|Tak|— Jeśli włączysz zbieranie danych IntelliTrace, zbieranie danych pokrycia kodu nie działa.<br />— W przypadku korzystania z IntelliTrace dla roli klienta sieci Web należy również wybrać serwer proxy klienta ASP.NET dla IntelliTrace i adaptera danych diagnostycznych wpływu na testowanie.<br />— Obsługiwane są tylko następujące wersje usług IIS: IIS 7,0, IIS 7,5 i IIS 8,0.|
|**Emulacja sieci:** Możesz określić, że chcesz umieścić sztuczne obciążenie sieciowe w teście przy użyciu ustawienia testu. Emulacja sieci wpływa na komunikację z maszyną i z niej przez emulowanie określonej szybkości połączenia sieciowego, takiej jak połączenie telefoniczne. |Nie|Tak (Zobacz uwagi)|Nie|Karty danych diagnostycznych emulacji sieci można użyć dla roli klienta lub serwera. Nie ma potrzeby używania karty na obu rolach, które komunikują się ze sobą. **Uwaga:**  Ten adapter danych diagnostycznych ma zastosowanie tylko do ustawień testu programu Visual Studio. Nie jest on używany dla ustawień testu w Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). **Uwaga:**  Emulacji sieci nie można użyć do zwiększenia szybkości połączenia sieciowego. **Ostrzeżenie:**  Jeśli dołączysz adapter danych diagnostycznych emulacji sieci w ustawieniach testu i zamierzasz używać go na komputerze lokalnym, należy również powiązać sterownik emulacji sieci z jedną z kart sieciowych maszyny. Sterownik emulacji sieci jest wymagany dla karty danych diagnostycznych emulacji sieci do działania. Sterownik emulacji sieci jest instalowany i powiązany z kartą na dwa sposoby: <ul><li>**Sterownik emulacji sieci instalowany z Microsoft Visual Studio agentem testowym:** Program Visual Studio Test Agent może być używany zarówno na komputerach zdalnych, jak i na komputerze lokalnym. Po zainstalowaniu agenta testowego programu Visual Studio proces instalacji obejmuje krok konfiguracji, który wiąże sterownik emulacji sieci z kartą sieciową. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).</li><li>**Sterownik emulacji sieci instalowany z Microsoft Visual Studio Test Professional:** W przypadku korzystania z emulacji sieci po raz pierwszy zostanie wyświetlony monit o powiązanie sterownika emulacji sieci z kartą sieciową.</li></ul> Sterownik emulacji sieci można również zainstalować z poziomu wiersza polecenia na komputerze lokalnym bez instalowania agenta testowego programu Visual Studio za pomocą następującego polecenia: **VSTESTCONFIG NETWORKEMULATION/install** **Warning:**  Karta emulacji sieci jest ignorowana przez testy obciążenia. Zamiast tego testy obciążenia używają ustawień, które są określone w mieszaninie sieci w scenariuszu testu obciążenia.|
|**Informacje o systemie:** Ustawienie testu można skonfigurować w taki sposób, aby obejmowało informacje o systemie komputera, na którym test jest uruchamiany.|Tak|Tak|Tak||
|**Wpływ na test:** Można zbierać informacje o tym, które metody kodu aplikacji były używane po uruchomieniu przypadku testowego. Ta wartość może być używana razem ze zmianami w kodzie aplikacji, który został utworzony przez deweloperów w celu określenia, które testy miały wpływ na te zmiany.|Tak|Tak|Tak|— W przypadku zbierania danych dotyczących wpływu testów dla roli klienta sieci Web należy również wybrać serwer proxy ASP.NET klienta dla IntelliTrace i adaptera danych diagnostycznych wpływu na testowanie.<br />— Obsługiwane są tylko następujące wersje usług IIS: IIS 7,0, IIS 7,5 i IIS 8,0.|
|**Rejestrator wideo:** Możesz utworzyć nagranie wideo swojej sesji pulpitu podczas przeprowadzania testu. Film wideo może pomóc innym członkom zespołu izolować problemy z aplikacjami, które są trudne do odtworzenia.|Tak|Tak (Zobacz uwagi)|Tak|— Jeśli włączysz oprogramowanie agenta testowego do uruchamiania jako proces zamiast usługi, możesz utworzyć nagranie wideo podczas uruchamiania testów automatycznych.|
