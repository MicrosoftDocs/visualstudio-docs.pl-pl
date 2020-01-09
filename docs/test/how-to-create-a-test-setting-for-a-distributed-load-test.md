---
title: Utwórz ustawienie testu dla testu obciążenia rozłożonego
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3129aa5139533db0783c168c3489e071fe9339b5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589154"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Instrukcje: Tworzenie pliku ustawień testu dla testu obciążenia rozłożonego

Konfigurowanie *ustawienia testu* dla testów obciążenia, dzięki czemu można rozprowadzić te testy na wielu komputerach przy użyciu agentów testowych i kontrolerów testów. Można również skonfigurować ustawienia testu do użycia *adapterów danych diagnostycznych*, które określają rodzaje danych, które mają być zbierane lub określają wpływ na maszyny testowe podczas uruchamiania testów obciążenia w programie Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Na przykład można użyć adaptera danych diagnostycznych programu ASP.NET Profiler do zbierania podział wydajność kodu. Ponadto adapterów danych diagnostycznych może służyć do symulacji wąskich gardeł na maszynie testowej lub zmniejszenie dostępnej pamięci systemowej.

Ustawienia testu dla programu Visual Studio są przechowywane w pliku. Ustawienia testowe definiują następujące informacje dotyczące poszczególnych ról:

- Zbiór ról, które są wymagane dla badanej aplikacji

- Rola służące do uruchamiania testów

- Adaptery danych diagnostycznych do użycia dla każdej roli

Po uruchomieniu testów, możesz wybrać ustawienia testu do użycia jako ustawienia aktywnego testu w zależności od tego, czego wymagasz dla tego określonego testu. Plik ustawień testu jest przechowywana jako część rozwiązania. Nazwa pliku ma rozszerzenie *.testsettings*.

Gdy dodajesz projekt testu wydajności sieci web i obciążenia do rozwiązania, *Default.testsettings* zostanie utworzony plik. Plik jest automatycznie dodawany do rozwiązania w folderze **elementy rozwiązania** folderu. Ten plik uruchamia testy lokalnie bez żadnych adapterów danych diagnostycznych. Możesz dodać innego *.testsettings* plików lub edytować *.testsettings* plik, aby określić adaptery danych diagnostycznych i kontrolery testów.

Kontroler testów będzie miał agentów, które mogą być używane dla każdej roli w ustawieniach testu. Aby uzyskać więcej informacji na temat kontrolerów testów i agentów testowych, zobacz [zarządzać kontrolerami testów i agentami testowymi za pomocą programu Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Wykonaj następujące kroki, aby utworzyć i usuwania ustawień testowych w rozwiązaniu dla testów obciążenia, które mają być uruchamiane w programie Visual Studio.

## <a name="create-a-test-settings-file"></a>Utwórz plik ustawień testu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **elementy rozwiązania**, wskaż polecenie **Dodaj**, a następnie wybierz **nowy element**.

     **Dodaj nowy element** pojawi się okno dialogowe.

2. W **zainstalowane szablony** okienku wybierz **ustawienia testu**.

3. (Opcjonalnie) W **nazwa** Zmień nazwę pliku ustawień testu.

4. Wybierz **Dodaj**.

     Nowy plik ustawień testowych pojawia się w **Eksploratora rozwiązań**w obszarze **elementy rozwiązania** folderu.

5. **Ustawienia testu** zostanie wyświetlone okno dialogowe. **Ogólne** została zaznaczona strona.

     Można teraz edytować i zapisać wartości ustawień testu.

6. W obszarze **nazwa**, wpisz nazwę ustawień testu.

7. (Opcjonalnie) W obszarze **opis**, wpisz opis ustawienia testu, aby inni członkowie zespołu wiedzieli, jego przeznaczenie.

8. (Opcjonalnie) Aby wybrać domyślny schemat nazewnictwa dla przebiegów testowych, wybierz **domyślny schemat nazewnictwa**. Aby zdefiniować własny schemat nazewnictwa, wybierz **schemat zdefiniowany przez użytkownika** i wpisz tekst, który ma w **tekst prefiksu**. Aby sygnatura daty i godziny należy dołączyć do nazwy testu, wybierz **Dołącz sygnaturę daty i godziny**.

9. Wybierz **role**.

     **Role** zostanie wyświetlona strona.

     ![Rola ustawień testu](../test/media/load_testtestrole.png)

10. Aby zdalnie uruchomić testy, lub aby zdalnie uruchomić testy i zbierać dane, należy użyć **metoda wykonania testu** listy rozwijanej i wybierz pozycję **zdalne wykonywanie kodu**.

11. Użyj **kontrolera** listy rozwijanej można wybrać kontrolera testowego dla agentów testowych spośród **kontrolera** który będzie używany do uruchamiania testów lub zbierania danych.

    > [!NOTE]
    > Jeśli po raz pierwszy dodajesz kontrolera, kontrolery nie będzie wyświetlane na liście rozwijanej. Lista jest wypełniana przez wcześniejsze kontrolery, które określono w innych ustawieniach testowych. Należy wpisać nazwę kontrolera, w polu (na przykład **TestControllerMachine1**).

12. Aby dodać role, które chcesz użyć do uruchamiania testów i zbieranie danych, w obszarze **role**, wybierz **Dodaj**.

13. Wpisz nazwę roli w **nazwa** kolumny. Na przykład rola może być "Serwer sieci Web".

14. Powtórz kroki 12 i 13, aby dodać wszystkie role, których potrzebujesz.

     Każda rola używa agenta testowego, który jest zarządzany przez kontroler testów.

15. Wybierz rolę, którą chcesz uruchomić testy, a następnie wybierz **Ustaw rolę wymaganą do uruchomienia testów**.

    > [!IMPORTANT]
    > Inne role, które umożliwiają tworzenie i definiowanie nie zostaną uruchomione testy, ale będą stosowane jedynie do zbierania danych i adapterów diagnostycznych określonych dla ról w **dane i Diagnostyka** strony.

16. Aby ograniczyć liczbę agentów, których można użyć dla roli, wybierz rolę, a następnie wybierz **Dodaj** na pasku narzędzi w ramach **atrybuty agenta dla wybranej roli**.

     **Reguła wyboru agenta** zostanie wyświetlone okno dialogowe.

     Wpisz nazwę w **nazwa atrybutu** i wartości w **wartość atrybutu**, a następnie wybierz **OK**. Dodawanie atrybutów zgodnie w potrzebą.

     Na przykład można dodać atrybut o nazwie "RAM > 16GB" o wartości "True" lub "False", aby odfiltrować test agenta maszyn, które mają więcej niż 16GB pamięci. Aby zastosować ten sam atrybut do jednego lub więcej agentów testowych, należy użyć **Zarządzaj kontrolerem testów** okno dialogowe. Aby uzyskać więcej informacji, zobacz [zarządzać kontrolerami testów i agentami testowymi za pomocą programu Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Wybierz **dane i Diagnostyka**.

     **Dane i Diagnostyka** zostanie wyświetlona strona.

     ![Dane ustawienia testu i Diagnostyka](../test/media/load_testtest.png)

18. W **dane i Diagnostyka** strony, należy zdefiniować co dana rola będzie wykonywać wybierając *adapterów danych diagnostycznych* , którego rola będzie używać do zbierania danych. W związku z tym jeśli jeden lub więcej danych i adapterów diagnostycznych są włączone dla roli, kontroler testowy wybierze dostępną maszynę testową zbieranie danych dla określonych danych i adapterów diagnostycznych, na podstawie atrybutów, które są zdefiniowane dla roli. Aby wybrać dane i adaptery danych diagnostycznych, które mają być zbierane dla każdej roli, wybierz rolę. Dla każdej z ról wybierz adaptery danych diagnostycznych, zgodnie z potrzebami testów. Aby skonfigurować każdy adapter danych diagnostycznych, który wybrano dla każdej roli, wybierz **Konfiguruj**.

     **Przykład ról i adapterów danych diagnostycznych:**

     Na przykład można utworzyć rolę klienta o nazwie "Klient pulpitu" z atrybutem "Używa SQL" ustawiony na "True" i rolą serwera o nazwie "SQL Server", który ma atrybut ustawiony na "RAM > 16GB". Jeśli określisz, że "Klient pulpitu" uruchomi testy wybierając **Ustaw rolę wymaganą do uruchomienia testów** w **role** strony, kontroler testowy wybierze maszyny z agentami testowymi, które zawierają atrybut "Używa SQL" ustawiony na wartość "True", na którym chcesz uruchomić testy. Kontroler testu zaznaczy także maszyny programu SQL server, które mają agentów testowych, które zawierają atrybut "RAM > 16GB" jedynie do zbierania danych, która jest zdefiniowana przez adaptory danych i adapterów diagnostycznych, które znajdują się w tej roli. Agent testów "Klienta pulpitu" może również zbierać dane dla maszyn, na których jest uruchamiany, jeśli także wybrać karty danych i diagnostyki dla tej roli.

     Aby uzyskać szczegółowe informacje o każdym adapterze danych diagnostycznych i sposobu ich konfigurowania można obejrzeć skojarzony temat w poniższej tabeli.

     Aby uzyskać więcej informacji dotyczących adapterów danych diagnostycznych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

     **Adaptery danych diagnostycznych dla testów obciążenia**

    |Adapter danych diagnostycznych|Używanie w testach obciążeniowych|Skojarzonego tematu|
    |-|-------------------------|-|
    |**Serwer Proxy klienta ASP.NET dla IntelliTrace i wpływu Test:** ten serwer proxy umożliwia zbieranie informacji na temat połączeń http od klienta do serwera sieci web dla adapterów danych diagnostycznych IntelliTrace i badanie wpływu.|![Ikona informacji](../test/media/vc364f4.gif)<br /><br /> Jeśli nie ma określonych specjalnych potrzeb zbierania informacji systemowych maszyny agenta testowego nie zawierają tej karty. **Uwaga:** nie zalecamy użycia karty IntelliTrace w testach obciążenia z powodu problemów, które występują ze względu na dużą ilość danych, które są zbierane. <br /><br /> Dane dotyczące wpływu wywieranego nie są zbierane za pomocą testów obciążenia.||
    |**IntelliTrace:** można skonfigurować informacji diagnostycznych śledzenia, który jest przechowywany w pliku dziennika. Plik dziennika ma rozszerzenie *.tdlog*. Kiedy uruchamiasz test i krok testu zakończy się niepowodzeniem, można utworzyć usterkę. Plik dziennika, który zawiera śledzenia diagnostycznego jest automatycznie dołączany do tej usterki. Dane, które są zbierane w pliku dziennika zwiększają produktywność debugowania, skracając czas wymagany do odtworzenia i diagnozy błędu w kodzie. W tym dzienniku plików sesja lokalna może być odtworzona na innym komputerze. Zmniejsza to ryzyko, że błędu nie można odtworzyć.<br /><br /> Aby uzyskać więcej informacji, zobacz [danych zbierania IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Ikona ważnej informacji](../test/media/vc364f3.gif)<br /><br /> Zalecamy użycia karty IntelliTrace w testach obciążenia z powodu problemów, które występują ze względu na dużą ilość danych, które są zbierane i rejestrowane. Należy podjąć próbę używania karty IntelliTrace tylko w testach obciążenia, które nie trwają długo i nie używają wielu agentów testowych.|[Porady: zbieranie danych IntelliTrace aby pomóc w debugowaniu trudnych problemów](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**Profiler ASP.NET:** można utworzyć ustawienie testu zawierające profilowania, ASP.NET, która zbiera dane dotyczące wydajności w aplikacji sieci web platformy ASP.NET.|Adapter danych diagnostycznych profilera ASP.NET profile proces Internet Information Services (IIS), dzięki czemu nie będą działać względem serwera wdrożeniowego sieci web. Profilowanie witryny sieci Web w teście obciążenia, musisz zainstalować agenta testowego na komputerze, na którym jest zasilany z usług IIS. Agent testowy nie będzie generować obciążenia, ale będzie wyłącznie agentem kolekcji. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).|[Porady: Konfiguracja profilera ASP.NET do testów obciążenia za pomocą ustawień testu](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Dziennik zdarzeń:** można skonfigurować ustawienie testu w taki by obejmowało gromadzenie dzienników zdarzeń, które zostaną uwzględnione w wynikach testu.||[Porady: Konfigurowanie zbierania zdarzeń dziennika przy użyciu ustawień testu](https://msdn.microsoft.com/48d67891-6018-4549-83e3-213d5d824a02)|
    |**Emulacja sieci:** można określić, że chcesz umieścić sztuczne obciążenie sieciowe w badaniu, korzystając z ustawienia testu. Emulacja sieci ma wpływ na komunikację do i z komputera poprzez emulację szybkości połączenia określonej sieci, takich jak połączenie dodzwaniane. **Uwaga:** emulacji sieci nie można użyć do zwiększenia szybkości połączenia sieciowego.|Karta emulacji sieci jest ignorowana przez testy obciążenia. Zamiast tego testy obciążenia używają ustawień, które są określone w mieszanym profilu sieciowym Scenariusz testów obciążenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Informacje o systemie:** można skonfigurować ustawienie testu do uwzględnienia informacji o systemie o maszynach, na których jest uruchamiany moduł zbierający dane diagnostyczne i informacje o systemie. Informacje o systemie jest określony w wynikach testu przy użyciu ustawień testu.|![Ikona informacji](../test/media/vc364f4.gif)<br /><br /> Można zbierać informacje o systemie zarówno agentów obciążenia, jak i badanego systemu.|Do zebrania tych informacji jest wymagana żadna konfiguracja.|
    |**Wpływ na testowanie:** może zbierać informacje o tym, jakie zastosowano metody kodu aplikacji po uruchomieniu przypadku testowego. Może to służyć razem ze zmianami w kodzie aplikacji poczynionymi przez deweloperów do określenia, który test miały wpływ te zmiany deweloperskie.|Dane dotyczące wpływu wywieranego nie są zbierane za pomocą testów obciążenia.||
    |**Rejestrator wideo:** możesz utworzyć nagranie wideo swojej sesji pulpitu, po uruchomieniu automatycznych testów. Może to być pomocne przy podglądzie akcji użytkownika dla kodowanego testu interfejsu użytkownika. Nagranie wideo może pomóc innym członkom zespołu wyizolować elementy aplikacji, które są trudne do odtworzenia. **Uwaga:** podczas zdalnego wykonywania testów Rejestrator wideo nie będzie działać, chyba że agent jest uruchomiony w trybie procesu interaktywnego.|![Ikona ważnej informacji](../test/media/vc364f3.gif) **Ostrzeżenie:** nie zalecamy użycia karty Video Recorder do testów obciążenia.|[Porady: obejmują nagrań ekranu i głosu podczas testów przy użyciu ustawień testu](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Wybierz **wdrożenia**.

     **Wdrożenia** zostanie wyświetlona strona.

20. Aby utworzyć oddzielny katalog dla wdrożenia za każdym razem, że uruchomienia testów, wybierz **umożliwiają wdrażanie**.

    > [!NOTE]
    > Jeśli to zrobisz, można kontynuować kompilację aplikacji po uruchomieniu testów.

21. Aby dodać plik do katalogu, którego używasz do przeprowadzania swoich testów, wybierz opcję **Dodaj plik**, a następnie wybierz plik, który chcesz dodać.

    > [!NOTE]
    > Po uruchomieniu obciążenia testów, zestawy dodatków plug-in, pliki danych i przekazane pliki są automatycznie wdrażane.

22. Aby dodać katalog do katalogu, którego używasz do przeprowadzania swoich testów, wybierz opcję **Dodaj katalog** a następnie wybierz katalog, który chcesz dodać.

23. Aby uruchomić skrypty przed i po testach, wybierz **skrypty instalacyjne i czyszczące**.

     **Skrypty instalacyjne i czyszczące** zostanie wyświetlona strona.

    1. Wpisz lokalizację pliku skryptu w **skrypt instalacyjny** lub wybierz wielokropek ( **...** ), aby zlokalizować konfigurację scenariusza.

    2. Wpisz lokalizację pliku skryptu w **skrypt czyszczący** lub wybierz wielokropek ( **...** ), aby zlokalizować czyszczenie scenariusza.

24. Aby uruchomić testy przy użyciu innego hosta, wybierz **hosty**.

    1. W **typ hosta**, upewnij się, że **domyślne** jest zaznaczone.

        > [!NOTE]
        > **ASP.NET** w **typ hosta** nie jest obsługiwany w badaniach obciążenia.

    2. Użyj **Uruchom test w 32-bitową lub 64-bitowych** procesu listy rozwijanej do wybierz, czy testy wydajności i jednostki w sieci web w teście obciążenia, aby był uruchamiany jako procesy 32-bitową lub 64-bitowych.

        > [!NOTE]
        > Aby zapewnić maksymalną elastyczność, należy skompilować wydajności sieci web i obciążenia projektów testów przy użyciu **dowolny Procesor** konfiguracji. Następnie można uruchomić zarówno 32-bitowych i 64-bitowych agentów. Kompilowanie wydajności sieci web i obciążenia projekty testowe przy użyciu **64-bitowych** konfiguracja zapewnia nie posiada zalet.

25. (Opcjonalnie) Aby ograniczyć czas dla każdego przebiegu testu i badań indywidualnych, wybierz opcję **limity czasu testu.**

    1. Aby przerwać test Kiedy limit czasu zostanie przekroczony, wybierz **Przerwij przebieg testu, jeśli łączny czas przekroczy** , a następnie wpisz wartość dla tego ograniczenia.

    2. Aby zakończyć niepowodzeniem test indywidualny, po przekroczeniu limitu czasu, wybierz **Oznacz pojedynczy test jako zakończony niepowodzeniem, jeśli czas jego wykonywania przekroczy**, a następnie wpisz wartość dla tego ograniczenia.

26. Pomiń **testu jednostkowego**. Testy obciążeniowe nie należy używać tych ustawień.

27. Pomiń **Web Test**. Testy obciążeniowe nie należy używać tych ustawień.

28. Aby zapisać ustawienia testu, wybierz **Zapisz jako**. Wpisz nazwę pliku, który ma w **nazwa obiektu**.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Usuwanie pliku ustawień testu z rozwiązania

W obszarze **elementy rozwiązania** folderu w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy ustawienia testu, które chcesz usunąć, a następnie wybierz **Usuń**.

Plik ustawień testowych jest usuwany z rozwiązania.

## <a name="see-also"></a>Zobacz także

- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
