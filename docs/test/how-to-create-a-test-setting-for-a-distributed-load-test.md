---
title: Utwórz ustawienie testu dla testu obciążenia rozłożonego
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 625f4720e94f6ec0b3b9751c28ad18e0a9f38bbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288012"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Instrukcje: Tworzenie pliku ustawień testu dla testu obciążenia rozłożonego

Skonfiguruj *Ustawienia testu* dla testów obciążenia, aby można było dystrybuować te testy na wielu maszynach przy użyciu agentów testowych i kontrolerów testów. Można również skonfigurować ustawienia testu do korzystania z *adapterów danych diagnostycznych*, które określają rodzaje danych, które mają być zbierane lub wpływać na maszyny testowe podczas uruchamiania testów obciążenia z programu Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Na przykład można użyć adaptera danych diagnostycznych profilera programu ASP.NET do zebrania podziału wydajności kodu. Ponadto adaptery danych diagnostycznych mogą służyć do symulowania potencjalnych wąskich gardeł na maszynie testowej lub zmniejszenia ilości dostępnej pamięci systemowej.

Ustawienia testu dla programu Visual Studio są przechowywane w pliku. Ustawienia testu definiują następujące informacje dotyczące poszczególnych ról:

- Zestaw ról, które są wymagane dla testowanej aplikacji

- Rola, która ma być używana do uruchamiania testów

- Adaptery danych diagnostycznych do użycia dla każdej roli

Po uruchomieniu testów należy wybrać ustawienia testu, które będą używane jako aktywne ustawienia testu, w zależności od tego, co jest wymagane dla danego przebiegu testu. Plik ustawień testu jest przechowywany jako część rozwiązania. Nazwa pliku ma rozszerzenie *. testsettings*.

Po dodaniu projektu testu wydajności i obciążenia sieci Web do rozwiązania tworzony jest *domyślny plik. testsettings* . Plik jest automatycznie dodawany do rozwiązania w folderze **elementy rozwiązania** . Ten plik uruchamia testy lokalnie bez żadnych adapterów danych diagnostycznych. Można dodać inny plik *. testsettings* lub edytować plik *. testsettings* , aby określić adaptery danych diagnostycznych i kontrolery testów.

Kontroler testów będzie miał agentów, których można użyć dla każdej roli w ustawieniach testu. Aby uzyskać więcej informacji na temat kontrolerów testów i agentów testowych, zobacz [Zarządzanie kontrolerami testów i agentami testowymi za pomocą programu Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Wykonaj następujące kroki, aby utworzyć i usunąć ustawienia testu w rozwiązaniu dla testów obciążenia, które planujesz uruchamiać z programu Visual Studio.

## <a name="create-a-test-settings-file"></a>Utwórz plik ustawień testu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **elementy rozwiązania**, wskaż polecenie **Dodaj**, a następnie wybierz polecenie **nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. W okienku **zainstalowane szablony** wybierz pozycję **Ustawienia testu**.

3. Obowiązkowe W polu **Nazwa** Zmień nazwę pliku ustawień testu.

4. Wybierz pozycję **Dodaj**.

     Nowy plik ustawień testu jest wyświetlany w **Eksplorator rozwiązań**w folderze **elementy rozwiązania** .

5. Zostanie wyświetlone okno dialogowe **Ustawienia testu** . Wybrana jest strona **Ogólne** .

     Możesz teraz edytować i zapisywać wartości ustawień testu.

6. W polu **Nazwa**wpisz nazwę dla ustawień testu.

7. Obowiązkowe W obszarze **Opis**wpisz opis ustawienia testu, aby inni członkowie zespołu wiedzieli, co jest zamierzone.

8. Obowiązkowe Aby wybrać domyślny schemat nazewnictwa dla przebiegów testowych, wybierz **domyślny schemat nazewnictwa**. Aby zdefiniować własny schemat nazewnictwa, wybierz **schemat zdefiniowany przez użytkownika** , a następnie wpisz tekst, który ma być używany jako **prefiks tekstu**. Aby dołączyć sygnaturę daty i godziny do nazwy przebiegu testu, wybierz pozycję **Dołącz sygnaturę daty i godziny**.

9. Wybierz **role**.

     Zostanie wyświetlona strona **role** .

     ![Rola ustawienia testu](../test/media/load_testtestrole.png)

10. Aby zdalnie uruchomić testy lub uruchomić testy zdalnie i zbierać dane zdalnie, Użyj listy rozwijanej **Metoda wykonania testu** i wybierz pozycję **wykonanie zdalne**.

11. Użyj listy rozwijanej **kontroler** , aby wybrać kontroler testów dla agentów testowych z **kontrolera** , który będzie używany do uruchamiania testów lub zbierania danych.

    > [!NOTE]
    > Jeśli po raz pierwszy dodajesz kontroler, na liście rozwijanej nie będą wyświetlane żadne kontrolery. Lista jest wypełniana przez wcześniejsze kontrolery, które określono w innych ustawieniach testu. Należy wpisać nazwę kontrolera w polu (na przykład **TestControllerMachine1**).

12. Aby dodać role, które mają być używane do uruchamiania testów i zbierania danych, w obszarze **role**wybierz pozycję **Dodaj**.

13. Wpisz nazwę roli w kolumnie **Nazwa** . Na przykład rola może być "serwer sieci Web".

14. Powtórz kroki 12 i 13, aby dodać wszystkie wymagane role.

     Każda rola używa agenta testowego, który jest zarządzany przez kontroler testów.

15. Wybierz rolę, w której chcesz uruchomić testy, a następnie wybierz pozycję **Ustaw jako rolę, aby uruchomić testy**.

    > [!IMPORTANT]
    > Inne utworzone i zdefiniowane role nie będą uruchamiać testów, ale będą używane tylko do zbierania danych zgodnie z kartami danych i diagnostycznymi określonymi dla ról na stronie **dane i Diagnostyka** .

16. Aby ograniczyć liczbę agentów, które mogą być używane dla roli, wybierz rolę, a następnie wybierz pozycję **Dodaj** na pasku narzędzi w obszarze **atrybuty agenta dla wybranej roli**.

     Zostanie wyświetlone okno dialogowe **reguła wyboru agenta** .

     Wpisz nazwę w polu **nazwa atrybutu** i wartość w polu **wartość atrybutu**, a następnie wybierz przycisk **OK**. Dodaj dowolną liczbę atrybutów.

     Na przykład, można dodać atrybut o nazwie "RAM > 16GB" o wartości "true" lub "false", aby odfiltrować maszyny z agentami testowymi, które mają więcej niż 16GB pamięci. Aby zastosować ten sam atrybut do co najmniej jednego agenta testowego, należy użyć okna dialogowego **zarządzanie Test Controller** . Aby uzyskać więcej informacji, zobacz [Zarządzanie kontrolerami testów i agentami testowymi za pomocą programu Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Wybierz **dane i Diagnostyka**.

     Zostanie wyświetlona strona **dane i Diagnostyka** .

     ![Dane i Diagnostyka ustawień testu](../test/media/load_testtest.png)

18. Na stronie **dane i Diagnostyka** można zdefiniować działanie roli, wybierając *adaptery danych diagnostycznych* , których rola będzie używać do zbierania danych. W związku z tym, jeśli co najmniej jedna karta danych i diagnostyki jest włączona dla roli, kontroler testów wybierze dostępny komputer agenta testowego do zbierania danych dla określonych danych i adapterów diagnostycznych na podstawie atrybutów zdefiniowanych dla roli. Aby wybrać adaptery danych i danych diagnostycznych, które mają być zbierane dla każdej roli, wybierz rolę. Dla każdej roli wybierz adaptery danych diagnostycznych zgodnie z potrzebami testów. Aby skonfigurować każdą kartę danych diagnostycznych wybraną dla każdej roli, wybierz pozycję **Konfiguruj**.

     **Przykład ról i adapterów danych diagnostycznych:**

     Można na przykład utworzyć rolę klienta o nazwie "Klient pulpitu" z atrybutem "Użyj języka SQL" ustawionego na wartość "true" i roli serwera o nazwie "SQL Server", która ma atrybut ustawiony na wartość "RAM > 16GB". Jeśli określisz, że "Klient pulpitu" uruchomi testy, wybierając pozycję **Ustaw jako rolę do uruchamiania testów** na stronie **role** , kontroler testów wybierze maszyny z agentami testowymi, które zawierają atrybut "używa języka SQL" ustawionego na wartość "true", na którym mają zostać uruchomione testy. Kontroler testu również wybiera maszyny programu SQL Server z agentami testowymi, które zawierają atrybut "RAM > 16GB" tylko do zbierania danych, które są zdefiniowane przez adaptery danych i diagnostyki zawarte w roli. Agent testów "Klient stacjonarny" może również zbierać dane dla maszyn, na których jest uruchomiona, jeśli wybrano opcję dane i adaptery diagnostyczne dla tej roli.

     Aby uzyskać szczegółowe informacje na temat każdego adaptera danych diagnostycznych i sposobu jego konfiguracji, można wyświetlić skojarzony temat w poniższej tabeli.

     Aby uzyskać więcej informacji na temat adapterów danych diagnostycznych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

     **Adaptery danych diagnostycznych dla testów obciążenia**

    |Adapter danych diagnostycznych|Używanie w testach obciążenia|Skojarzony temat|
    |-|-------------------------|-|
    |**ASP.NET serwer proxy klienta dla IntelliTrace i wpływu na testowanie:** Ten serwer proxy umożliwia zbieranie informacji o wywołaniach http z klienta do serwera sieci Web dla IntelliTrace i adapterów danych diagnostycznych dotyczących wpływu testów.|![Ikona informacji](../test/media/vc364f4.gif)<br /><br /> Jeśli nie ma potrzeby zbierania informacji o systemie dla maszyn agenta testowego, nie należy uwzględniać tej karty. **Przestroga:**  Nie zaleca się używania karty IntelliTrace w testach obciążenia z powodu problemów występujących ze względu na dużą ilość zbieranych danych. <br /><br /> Dane o wpływie na testy nie są zbierane za pomocą testów obciążenia.||
    |**IntelliTrace:** Można skonfigurować określone informacje śledzenia diagnostycznego, które są przechowywane w pliku dziennika. Plik dziennika ma rozszerzenie *. tdlog*. Gdy uruchamiasz test, a krok testu zakończy się niepowodzeniem, możesz utworzyć błąd. Plik dziennika zawierający ślad diagnostyczny jest automatycznie dołączany do tego błędu. Dane zbierane w pliku dziennika zwiększają produktywność debugowania, skracając czas wymagany do odtworzenia i zdiagnozowania błędu w kodzie. Z tego pliku dziennika sesja lokalna można utworzyć ponownie na innym komputerze. Zmniejsza to ryzyko, że nie można odtworzyć usterki.<br /><br /> Aby uzyskać więcej informacji, zobacz [zbieranie danych IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Ikona ważnej informacji](../test/media/vc364f3.gif)<br /><br /> Nie zaleca się używania karty IntelliTrace w testach obciążenia z powodu problemów, które występują z powodu dużej ilości zbieranych i rejestrowanych danych. Należy próbować użyć karty IntelliTrace tylko w testach obciążenia, które nie działają długo i nie używają wielu agentów testowych.|[Instrukcje: zbieranie danych IntelliTrace w celu ułatwienia debugowania trudnych problemów](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**Profiler ASP.NET:** Można utworzyć ustawienie testu, które obejmuje profilowanie ASP.NET, które zbiera dane dotyczące wydajności w aplikacjach sieci Web ASP.NET.|Karta danych diagnostycznych programu ASP.NET Profiler przetwarza proces Internet Information Services (IIS), więc nie będzie działała na deweloperskim serwerze sieci Web. Aby profilować witrynę sieci Web w teście obciążenia, należy zainstalować agenta testowego na komputerze, na którym są uruchomione usługi IIS. Agent testowy nie będzie generować obciążenia, ale będzie tylko agentem kolekcji. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).|[Instrukcje: Konfigurowanie profilera ASP.NET dla testów obciążenia przy użyciu ustawień testu](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Dziennik zdarzeń:** Można skonfigurować ustawienie testu, aby uwzględnić zbieranie dzienników zdarzeń, które zostaną uwzględnione w wynikach testu.||[Instrukcje: Konfigurowanie zbierania dzienników zdarzeń przy użyciu ustawień testu](https://msdn.microsoft.com/48d67891-6018-4549-83e3-213d5d824a02)|
    |**Emulacja sieci:** Możesz określić, że chcesz umieścić sztuczne obciążenie sieciowe w teście przy użyciu ustawienia testu. Emulacja sieci wpływa na komunikację z maszyną i z niej przez emulowanie określonej szybkości połączenia sieciowego, takiej jak połączenie telefoniczne. **Uwaga:**  Emulacji sieci nie można użyć do zwiększenia szybkości połączenia sieciowego.|Karta emulacji sieci jest ignorowana przez testy obciążenia. Zamiast tego testy obciążenia używają ustawień, które są określone w mieszaninie sieci w scenariuszu testu obciążenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Informacje o systemie:** Ustawienie testu można skonfigurować w taki sposób, aby obejmowało informacje o systemie maszyn, na których uruchomiono diagnostykę informacji o systemie i moduł zbierający dane. Informacje o systemie są określone w wynikach testu przy użyciu ustawienia testu.|![Ikona informacji](../test/media/vc364f4.gif)<br /><br /> Można zbierać informacje o systemie zarówno z agentów obciążenia, jak i z testowanego systemu.|Do zebrania tych informacji nie jest wymagana żadna konfiguracja.|
    |**Wpływ na test:** Można zbierać informacje o tym, które metody kodu aplikacji były używane po uruchomieniu przypadku testowego. Ta wartość może być używana razem ze zmianami w kodzie aplikacji, które są tworzone przez deweloperów, aby określić, które testy miały wpływ na te zmiany.|Dane o wpływie na testy nie są zbierane z testami obciążenia.||
    |**Rejestrator wideo:** Możesz utworzyć nagranie wideo swojej sesji pulpitu podczas uruchamiania testu automatycznego. Może to być przydatne do wyświetlania akcji użytkownika dla kodowanego testu interfejsu użytkownika. Film wideo może pomóc innym członkom zespołu izolować problemy z aplikacjami, które są trudne do odtworzenia. **Uwaga:**  Gdy testy są uruchamiane zdalnie, rejestrator wideo nie będzie działać, chyba że agent zostanie uruchomiony w trybie przetwarzania interaktywnego.|![Ważne ](../test/media/vc364f3.gif) **Ostrzeżenie ikony:**  nie zaleca się używania karty rejestratora wideo do testów obciążenia.|[Instrukcje: uwzględnianie nagrań ekranu i głosu podczas testów przy użyciu ustawień testu](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Wybierz pozycję **wdrożenie**.

     Zostanie wyświetlona strona **wdrażanie** .

20. Aby utworzyć oddzielny katalog do wdrożenia przy każdym uruchomieniu testów, wybierz pozycję **Włącz wdrażanie**.

    > [!NOTE]
    > W takim przypadku można kontynuować Kompilowanie aplikacji po uruchomieniu testów.

21. Aby dodać plik do katalogu, którego używasz do uruchamiania testów, wybierz polecenie **Dodaj plik**, a następnie wybierz plik, który chcesz dodać.

    > [!NOTE]
    > Po uruchomieniu testów obciążenia, zestawy dodatków plug-in, pliki danych i przekazane pliki zostaną automatycznie wdrożone.

22. Aby dodać katalog do katalogu, którego używasz do uruchamiania testów, wybierz **Dodaj katalog** , a następnie wybierz katalog, który chcesz dodać.

23. Aby uruchomić skrypty przed i po testach, wybierz pozycję **Instalator i oczyść skrypty**.

     Zostanie wyświetlona strona **Konfiguracja i czyszczenie skryptów** .

    1. Wpisz lokalizację pliku skryptu w **skrypcie Instalatora** lub wybierz wielokropek (**...**), aby zlokalizować skrypt Instalatora.

    2. Wpisz lokalizację pliku skryptu w **skrypcie czyszczenia** lub wybierz wielokropek (**...**), aby zlokalizować skrypt czyszczący.

24. Aby uruchomić testy przy użyciu innego hosta, wybierz **hosty**.

    1. Sprawdź, czy w polu **typ hosta**jest wybrana **wartość domyślna** .

        > [!NOTE]
        > **ASP.NET** w **typie hosta** nie są obsługiwane w testach obciążenia.

    2. Użyj opcji **Uruchom test w procesie 32-bitowym lub 64-bitowym** , aby określić, czy chcesz, aby testy wydajności sieci Web i testów jednostkowych w teście obciążenia były uruchamiane jako procesy 32-bitowe czy 64-bitowe.

        > [!NOTE]
        > Aby zapewnić maksymalną elastyczność, należy skompilować projekty testów wydajności i obciążenia sieci Web przy użyciu **dowolnej konfiguracji procesora** . Następnie można uruchomić zarówno na 32-bitowym, jak i 64-bitowym agencie. Kompilowanie projektów testów wydajności i obciążenia sieci Web przy użyciu konfiguracji **64-bitowej** nie oferuje żadnej zalety.

25. Obowiązkowe Aby ograniczyć czas dla każdego przebiegu testowego i poszczególnych testów, wybierz opcję **przekroczenie limitu czasu testu.**

    1. Aby przerwać przebieg testu po przekroczeniu limitu czasu, wybierz opcję **Przerwij przebieg testu, jeśli łączny czas przekroczy** , a następnie wpisz wartość dla tego ograniczenia.

    2. Aby zakończyć działanie pojedynczego testu po przekroczeniu limitu czasu, wybierz opcję **Oznacz pojedynczy test jako zakończony niepowodzeniem, jeśli czas jego wykonywania przekroczy**, a następnie wpisz wartość dla tego limitu.

26. Pomiń **test jednostkowy**. Testy obciążenia nie używają tych ustawień.

27. Pomiń **test sieci Web**. Testy obciążenia nie używają tych ustawień.

28. Aby zapisać ustawienia testu, wybierz pozycję **Zapisz jako**. Wpisz nazwę pliku, który ma zostać wpisany w polu **Nazwa obiektu**.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Usuwanie pliku ustawień testu z rozwiązania

W folderze **elementy rozwiązania** w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy ustawienia testu, które chcesz usunąć, a następnie wybierz polecenie **Usuń**.

Plik ustawień testu zostanie usunięty z rozwiązania.

## <a name="see-also"></a>Zobacz też

- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
