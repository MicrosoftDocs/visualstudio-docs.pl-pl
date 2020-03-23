---
title: Tworzenie ustawienia testu dla testu obciążenia rozproszonego
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3129aa5139533db0783c168c3489e071fe9339b5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589154"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Jak: Tworzenie pliku ustawień testu dla testu obciążenia rozproszonego

Skonfiguruj *ustawienia testów obciążenia,* aby można było rozpowszechniać te testy na wielu komputerach przy użyciu agentów testowych i kontrolerów testów. Można również skonfigurować ustawienia testowe do używania *kart danych diagnostycznych,* które określają rodzaje danych, które mają być zbierane lub jak wpływać na maszyny testowe po uruchomieniu testów obciążenia z programu Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Na przykład można użyć karty danych diagnostycznych ASP.NET Profilera do zbierania podziału wydajności kodu. Ponadto karty danych diagnostycznych mogą służyć do symulowania potencjalnych wąskich gardeł na komputerze testowym lub zmniejszenia dostępnej pamięci systemowej.

Ustawienia testu dla programu Visual Studio są przechowywane w pliku. Ustawienia testu definiują następujące informacje o każdej roli:

- Zestaw ról wymaganych dla aplikacji w ramach testu

- Rola używana do uruchamiania testów

- Karty danych diagnostycznych do użycia dla każdej roli

Po uruchomieniu testów, należy wybrać ustawienia testu, aby użyć jako aktywne ustawienia testu w zależności od tego, co jest wymagane dla tego konkretnego przebiegu testu. Plik ustawień testu jest przechowywany jako część rozwiązania. Nazwa pliku ma rozszerzenie *.testsettings*.

Po dodaniu projektu testu wydajności sieci web i ładowania do rozwiązania tworzony jest plik *Default.testsettings.* Plik zostanie automatycznie dodany do rozwiązania w folderze **Elementy rozwiązania.** Ten plik uruchamia testy lokalnie bez żadnych kart danych diagnostycznych. Można dodać inny plik *.testsettings* lub edytować plik *.testsettings,* aby określić karty danych diagnostycznych i kontrolery testów.

Kontroler testów będzie miał agentów, które mogą być używane dla każdej roli w ustawieniach testu. Aby uzyskać więcej informacji na temat kontrolerów testów i agentów testowych, zobacz [Zarządzanie kontrolerami testów i agentami testowymi za pomocą programu Visual Studio.](../test/manage-test-controllers-and-test-agents.md)

Wykonaj następujące kroki, aby utworzyć i usunąć ustawienia testu w rozwiązaniu dla testów obciążenia, które mają być uruchamiane z programu Visual Studio.

## <a name="create-a-test-settings-file"></a>Tworzenie pliku ustawień testu

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję Elementy rozwiązania**, wskaż polecenie **Dodaj**, a następnie wybierz polecenie Nowy **element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. W okienku **Zainstalowane szablony** wybierz pozycję **Ustawienia testu**.

3. (Opcjonalnie) W polu **Nazwa** zmień nazwę pliku ustawień testu.

4. Wybierz **pozycję Dodaj**.

     Nowy plik ustawień testu pojawi się w **Eksploratorze rozwiązań**w folderze **Elementy rozwiązania.**

5. Zostanie wyświetlone okno dialogowe **Ustawienia testu.** Zostanie wybrana strona **Ogólne.**

     Teraz można edytować i zapisywać wartości ustawień testu.

6. W obszarze **Nazwa**wpisz nazwę ustawień testu.

7. (Opcjonalnie) W obszarze **Opis**wpisz opis ustawienia testu, aby inni członkowie zespołu wiedzieli, do czego jest przeznaczony.

8. (Opcjonalnie) Aby wybrać domyślny schemat nazewnictwa dla przebiegów testów, wybierz **domyślny schemat nazewnictwa**. Aby zdefiniować własny schemat nazewnictwa, wybierz **schemat zdefiniowany przez użytkownika,** a następnie wpisz odpowiedni tekst w **tekście prefiksu**. Aby dołączyć datę i godzinę do nazwy przebiegu testu, wybierz pozycję **Dołącz sygnaturę daty i godziny**.

9. Wybierz **pozycję Role**.

     Zostanie wyświetlona strona **Role.**

     ![Rola ustawiania testu](../test/media/load_testtestrole.png)

10. Aby uruchomić testy zdalnie lub uruchomić testy zdalnie i zdalnie zbierać dane, użyj listy rozwijanej **Test Execution Method** i wybierz **zdalne wykonanie.**

11. Użyj listy rozwijanej **Kontroler,** aby wybrać kontroler testów dla agentów testowych z **kontrolera,** który będzie używany do uruchamiania testów lub zbierania danych.

    > [!NOTE]
    > Jeśli jest to pierwszy raz, gdy dodajesz kontroler, żadne kontrolery nie zostaną wyświetlone na liście rozwijanej. Lista jest wypełniana przez poprzednie kontrolery, które zostały określone w innych ustawieniach testu. Należy wpisać nazwę kontrolera w polu (na przykład **TestControllerMachine1**).

12. Aby dodać role, których chcesz użyć do uruchamiania testów i zbierania danych, w obszarze **Role**wybierz pozycję **Dodaj**.

13. Wpisz nazwę roli w kolumnie **Nazwa.** Na przykład rola może być "Serwer sieci Web".

14. Powtórz kroki 12 i 13, aby dodać wszystkie potrzebne role.

     Każda rola używa agenta testowego, który jest zarządzany przez kontroler testów.

15. Wybierz rolę, którą chcesz uruchomić testy, a następnie wybierz pozycję **Ustaw jako rolę do uruchamiania testów**.

    > [!IMPORTANT]
    > Inne role, które tworzysz i definiujesz, nie będą uruchamiać testów, ale będą używane tylko do zbierania danych zgodnie z danymi i kartami diagnostycznymi określonymi dla ról na stronie **Dane i diagnostyka.**

16. Aby ograniczyć agentów, którzy mogą być używane dla roli, wybierz rolę, a następnie wybierz pozycję **Dodaj** na pasku narzędzi w obszarze **Atrybuty agenta dla wybranej roli**.

     Zostanie wyświetlone okno dialogowe **Reguła wyboru** agenta.

     Wpisz nazwę w polu **Nazwa atrybutu** i wartość w **polu Wartość atrybutu**, a następnie wybierz przycisk **OK**. Dodaj tyle atrybutów, ile potrzebujesz.

     Na przykład można dodać atrybut o nazwie "RAM > 16GB", który ma wartość "True" lub "False" do filtrowania na komputerach agenta testowego, które mają więcej niż 16 GB pamięci. Aby zastosować ten sam atrybut do jednego lub więcej agentów testowych, należy użyć okna dialogowego **Zarządzanie kontrolerem testów.** Aby uzyskać więcej informacji, zobacz [Zarządzanie kontrolerami testów i agentami testowymi za pomocą programu Visual Studio.](../test/manage-test-controllers-and-test-agents.md)

17. Wybierz **pozycję Dane i diagnostyka**.

     Zostanie wyświetlona strona **Dane i diagnostyka.**

     ![Dane ustawień testowych i diagnostyka](../test/media/load_testtest.png)

18. Na stronie **Dane i diagnostyka** można zdefiniować, co robi rola, wybierając *karty danych diagnostycznych,* które rola będzie używać do zbierania danych. W związku z tym jeśli jeden lub więcej kart danych i diagnostyki są włączone dla roli, kontroler testów wybierze dostępny komputer agenta testowego do zbierania danych dla określonych danych i kart diagnostycznych na podstawie atrybutów zdefiniowanych dla roli. Aby wybrać karty danych i danych diagnostycznych, które chcesz zebrać dla każdej roli, wybierz rolę. Dla każdej roli wybierz karty danych diagnostycznych zgodnie z potrzebami testów. Aby skonfigurować każdą kartę danych diagnostycznych wybraną dla każdej roli, wybierz pozycję **Konfiguruj**.

     **Przykład ról i kart danych diagnostycznych:**

     Na przykład można utworzyć rolę klienta o nazwie "Klient pulpitu", który ma atrybut "Używa SQL" ustawiony na "True" i roli serwera o nazwie "SQL Server", który ma atrybut ustawiony na "RAM > 16GB". Jeśli określisz, że "Klient pulpitu" uruchomi testy, wybierając **ustaw jako rolę do uruchamiania testów** na stronie **Role,** kontroler testów wybierze maszyny, które mają agentów testowych, które zawierają atrybut "Używa SQL" ustawiony na "True", na którym mają być uruchamiane testy. Kontroler testów wybierze również komputery z serwerem SQL, które mają agentów testowych, które zawierają atrybut "RAM > 16GB" tylko do zbierania danych zdefiniowanych przez karty danych i diagnostyki, które są zawarte w roli. Agent testów "Klient pulpitu" może również zbierać dane dla komputerów, na których jest uruchamiany, jeśli wybierzesz dane i karty diagnostyczne dla tej roli.

     Aby uzyskać szczegółowe informacje na temat każdej karty danych diagnostycznych i sposobu jej konfigurowania, można wyświetlić skojarzony temat w poniższej tabeli.

     Aby uzyskać więcej informacji na temat kart danych diagnostycznych, zobacz [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

     **Karty danych diagnostycznych do testów obciążenia**

    |Karta danych diagnostycznych|Stosowanie w testach obciążenia|Skojarzony temat|
    |-|-------------------------|-|
    |**ASP.NET serwer proxy klienta dla intellitrace i wpływ testu:** Ten serwer proxy umożliwia zbieranie informacji o wywołaniach http z klienta do serwera sieci web dla kart danych diagnostycznych IntelliTrace i Test Impact.|![Ikona Informacji](../test/media/vc364f4.gif)<br /><br /> Jeśli nie masz określonej potrzeby zbierania informacji o systemie dla maszyn agenta testowego, nie należy dołączać tej karty. **Uwaga:**  Nie zaleca się używania karty IntelliTrace w testach obciążenia z powodu problemów, które występują z powodu dużej ilości danych, które są zbierane. <br /><br /> Dane o wpływie testu nie są zbierane przy użyciu testów obciążenia.||
    |**IntelliTrace:** Można skonfigurować określone informacje śledzenia diagnostycznego, który jest przechowywany w pliku dziennika. Plik dziennika ma rozszerzenie *.tdlog*. Po uruchomieniu testu i krok testu kończy się niepowodzeniem, można utworzyć błąd. Plik dziennika zawierający śledzenie diagnostyczne jest automatycznie dołączany do tego błędu. Dane, które są zbierane w pliku dziennika zwiększa wydajność debugowania, zmniejszając czas wymagany do odtworzenia i zdiagnozować błąd w kodzie. Z tego pliku dziennika można odtworzyć sesję lokalną na innym komputerze. Zmniejsza to ryzyko, że błąd nie może być powielany.<br /><br /> Aby uzyskać więcej informacji, zobacz [Zbieranie danych IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Ikona ważnej informacji](../test/media/vc364f3.gif)<br /><br /> Nie zaleca się używania karty IntelliTrace w testach obciążenia z powodu problemów, które występują z powodu dużej ilości danych, które są zbierane i rejestrowane. Należy podjąć próbę użycia karty IntelliTrace tylko w testach obciążenia, które nie działają długo i nie używają wielu agentów testowych.|[Jak: Zbieranie danych IntelliTrace, aby pomóc w debugowaniu trudnych problemów](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET Profiler:** Można utworzyć ustawienie testowe, które obejmuje profilowanie ASP.NET, które zbiera dane o wydajności ASP.NET aplikacji sieci web.|Karta danych diagnostycznych ASP.NET profiler profiluje proces internetowych usług informacyjnych (IIS), dzięki czemu nie będzie działać na serwerze sieci Web dewelopera. Aby profilować witrynę sieci Web w teście obciążenia, należy zainstalować agenta testowego na komputerze, na którego uruchomione są usługi IIS. Agent testowy nie będzie generować obciążenia, ale będzie agentem tylko do kolekcji. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).|[Jak: Konfigurowanie ASP.NET profiler do testów obciążenia przy użyciu ustawień testu](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Dziennik zdarzeń:** Można skonfigurować ustawienie testu, aby uwzględnić zbieranie dzienników zdarzeń, które zostaną uwzględnione w wynikach testu.||[Jak: Konfigurowanie kolekcji dziennika zdarzeń przy użyciu ustawień testu](https://msdn.microsoft.com/48d67891-6018-4549-83e3-213d5d824a02)|
    |**Emulacja sieci:** Można określić, że chcesz umieścić sztuczne obciążenie sieciowe na test przy użyciu ustawienia testu. Emulacja sieci wpływa na komunikację do i z komputera, emulując określoną szybkość połączenia sieciowego, taką jak dial-up. **Uwaga:**  Nie można użyć emulacji sieci w celu zwiększenia szybkości połączenia sieciowego.|Karta emulacji sieci jest ignorowana przez testy obciążenia. Zamiast tego testy obciążenia używają ustawień, które są określone w kombinacji sieciowej scenariusza testu obciążenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Informacje o systemie:** Ustawienie testu można skonfigurować w taki sposób, aby zawierało informacje systemowe dotyczące maszyn, na których jest uruchamiana diagnostyka informacji o systemie i moduł zbierający dane. Informacje o systemie są określone w wynikach testu przy użyciu ustawienia testu.|![Ikona Informacji](../test/media/vc364f4.gif)<br /><br /> Można zbierać informacje o systemie zarówno z agentów obciążenia, jak i z testowego systemu.|Do zbierania tych informacji nie jest wymagana żadna konfiguracja.|
    |**Wpływ testu:** Można zbierać informacje o tym, które metody kodu aplikacji zostały użyte podczas uruchamiania przypadku testowego. Może to być używane wraz ze zmianami w kodzie aplikacji, które są wprowadzane przez deweloperów, aby określić, które testy zostały naruszone przez te zmiany rozwoju.|Dane o wpływie testu nie są zbierane za pomocą testów obciążenia.||
    |**Rejestrator wideo:** Po uruchomieniu automatycznego testu można utworzyć nagranie wideo sesji pulpitu. Może to być przydatne do wyświetlania akcji użytkownika dla zakodowany test interfejsu użytkownika. Film może pomóc innym członkom zespołu izolować problemy z aplikacjami, które są trudne do odtworzenia. **Uwaga:**  Podczas zdalnego uruchamiania testów rejestrator wideo nie będzie działać, chyba że agent działa w trybie interakcyjnym procesu.|![Ważna](../test/media/vc364f3.gif) **ikona Ostrzeżenie:** Nie zaleca się używania karty video recorder do testów obciążenia.|[Jak: Dołączanie nagrań ekranu i głosu podczas testów przy użyciu ustawień testowych](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Wybierz **pozycję Wdrażanie**.

     Zostanie wyświetlona strona **Wdrażanie.**

20. Aby utworzyć oddzielny katalog do wdrożenia przy każdym uruchomieniu testów, wybierz włącz **wdrożenie**.

    > [!NOTE]
    > Jeśli to zrobisz, można kontynuować tworzenie aplikacji po uruchomieniu testów.

21. Aby dodać plik do katalogu używanego do uruchamiania testów, wybierz pozycję **Dodaj plik**, a następnie wybierz plik, który chcesz dodać.

    > [!NOTE]
    > Po uruchomieniu testów obciążenia zestawy wtyczek, pliki danych i przekazane pliki są automatycznie wdrażane.

22. Aby dodać katalog do katalogu używanego do uruchamiania testów, wybierz pozycję **Dodaj katalog,** a następnie wybierz katalog, który chcesz dodać.

23. Aby uruchomić skrypty przed i po testach, wybierz pozycję **Instalacja i oczyszczanie skryptów**.

     Zostanie wyświetlona strona **Instalacja i oczyszczanie skryptów.**

    1. Wpisz lokalizację pliku skryptu w **skrypcie Instalatora** lub wybierz wielokropek (**...**), aby zlokalizować skrypt konfiguracji.

    2. Wpisz lokalizację pliku skryptu w **skrypcie Oczyszczania** lub wybierz wielokropek (**...**), aby zlokalizować skrypt oczyszczania.

24. Aby uruchomić testy przy użyciu innego hosta, wybierz pozycję **Hosty**.

    1. W **polu Typ hosta**sprawdź, czy zaznaczono opcję **Domyślna.**

        > [!NOTE]
        > **ASP.NET** typu **hosta** nie jest obsługiwana w testach obciążenia.

    2. Użyj **testu Uruchom w 32-bitowym lub 64-bitowym** procesie rozwijanej, aby wybrać, czy chcesz, aby testy wydajności sieci web i jednostki w teście obciążenia były uruchamiane jako procesy 32-bitowe czy 64-bitowe.

        > [!NOTE]
        > Aby uzyskać maksymalną elastyczność, należy skompilować wydajność sieci web i załadować projektów testowych przy użyciu dowolnej konfiguracji **procesora CPU.** Następnie można uruchomić zarówno na agentach 32-bitowych, jak i 64-bitowych. Kompilowanie projektów testów wydajności sieci web i ładowania przy użyciu konfiguracji **64-bitowej** nie oferuje żadnych korzyści.

25. (Opcjonalnie) Aby ograniczyć czas dla każdego przebiegu testu i poszczególnych testów, wybierz **limity czasu testowania.**

    1. Aby przerwać przebieg testu po przekroczeniu limitu czasu, wybierz **przerwij przebieg testu, jeśli całkowity czas przekracza,** a następnie wpisz wartość dla tego limitu.

    2. Aby zakończyć się niepowodzeniem testu indywidualnego po przekroczeniu limitu czasu, wybierz **opcję Oznacz pojedynczy test jako nieudany, jeśli jego czas wykonania przekracza**, i wpisz wartość dla tego limitu.

26. **Pomiń test jednostkowy**. Testy obciążenia nie używają tych ustawień.

27. Pomiń **test sieci Web**. Testy obciążenia nie używają tych ustawień.

28. Aby zapisać ustawienia testu, wybierz pozycję **Zapisz jako**. Wpisz nazwę pliku, który ma zostać wpisać w **polu Nazwa obiektu**.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Usuwanie pliku ustawień testu z rozwiązania

W obszarze folderu **Elementy rozwiązania** w **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy ustawienia testu, które chcesz usunąć, a następnie wybierz polecenie **Usuń**.

Plik ustawień testu zostanie usunięty z rozwiązania.

## <a name="see-also"></a>Zobacz też

- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
