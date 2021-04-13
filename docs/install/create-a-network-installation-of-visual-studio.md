---
title: Tworzenie instalacji sieciowej
description: Dowiedz się, jak utworzyć punkt instalacji sieci na potrzeby wdrażania programu Visual Studio w ramach przedsiębiorstwa.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6a93a8a41e4d2c4c91a55cfe91459f7a501b8efc
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296989"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Tworzenie instalacji sieciowej programu Visual Studio

Czasami administrator przedsiębiorstwa chce utworzyć punkt instalacji sieciowej, który zawiera pliki programu Visual Studio, które można wdrożyć na stacjach roboczych klienta. Ma to na celu ułatwienie scenariuszy, w których komputery klienckie mogą mieć ograniczone uprawnienia lub ograniczony dostęp do Internetu, lub gdy zespoły wewnętrzne chcą przeprowadzić testy zgodności, zanim organizacja zastosują się do określonej wersji zestawu narzędzi deweloperskich. Program Visual Studio został zaprojektowany tak, aby administrator mógł _utworzyć układ sieciowy_ , który zasadniczo tworzy pamięć podręczną plików znajdującą się w wewnętrznym lokalnym udziale sieciowym zawierającym wszystkie pliki programu Visual Studio zarówno do instalacji początkowej, jak i wszystkich przyszłych aktualizacji produktu.

 > [!NOTE]
 >  - Jeśli masz wiele wydań programu Visual Studio używanych w przedsiębiorstwie (na przykład zarówno program Visual Studio 2019 Professional, jak i Visual Studio 2019 Enterprise), należy utworzyć osobne udziały instalacji sieci dla każdej wersji.
 >  - Zalecane jest, aby zdecydować, jak klienci mają otrzymywać aktualizacje produktów _przed rozpoczęciem_ początkowej instalacji klienta.  Ułatwia to upewnienie się, że opcje konfiguracji zostały prawidłowo ustawione. Wybór obejmuje możliwość pobrania przez klientów aktualizacji z lokalizacji układu sieciowego lub z Internetu. 
 >  - Oryginalny układ instalacji programu Visual Studio i wszystkie kolejne aktualizacje produktu muszą znajdować się w tym samym katalogu sieciowym, aby upewnić się, że funkcje naprawy i dezinstalacji działają prawidłowo. 

## <a name="download-the-visual-studio-bootstrapper"></a>Pobieranie programu inicjującego programu Visual Studio

Pobierz plik programu inicjującego dla używanej wersji programu Visual Studio. Upewnij się, że wybrano pozycję **Zapisz**, a następnie wybierz pozycję **Otwórz folder**.

::: moniker range="vs-2017"

Aby uzyskać najnowszy program inicjujący dla programu Visual Studio 2017 w wersji 15,9, przejdź do strony [poprzednich wersji programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) i Pobierz jeden z następujących plików programu inicjującego:

| Wersja | Nazwa pliku |
|-------------|-----------------------|
|Visual Studio 2017 Enterprise w wersji 15,9 | vs_enterprise.exe |
|Visual Studio 2017 Professional w wersji 15,9 | vs_professional.exe |
|Narzędzia kompilacji programu Visual Studio 2017 w wersji 15,9  | vs_buildtools.exe |

Inne obsługiwane programu inicjujące obejmują vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe i vs_testprofessional.exe.

::: moniker-end

::: moniker range="vs-2019"

Zacznij od pobrania programu inicjującego Visual Studio 2019 ze [strony plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) lub strony wersji programu visual [Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) dla wybranej wersji i wydania programu Visual Studio.  Plik wykonywalny instalatora &mdash; lub bardziej szczegółowy, a program inicjujący &mdash; będzie zgodny z jedną z następujących:

|Wersja | Pobierz|
|-------------|-----------------------|
|Visual Studio Enterprise | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Inne obsługiwane programu inicjujące obejmują [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)i [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjującego i chcesz sprawdzić jego wersję. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inicjującego, wybierz polecenie **Właściwości**, wybierz kartę **szczegóły** , a następnie Wyświetl numer **wersji produktu** . Aby dopasować tę liczbę do wersji programu Visual Studio, zobacz [numery kompilacji i daty wydania programu Visual Studio](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjującego i chcesz sprawdzić jego wersję. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inicjującego, wybierz polecenie **Właściwości**, wybierz kartę **szczegóły** , a następnie Wyświetl numer **wersji produktu** . Aby dopasować tę liczbę do wersji programu Visual Studio, zobacz [wersje programu Visual studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history).

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Tworzenie folderu instalacyjnego w trybie offline

Aby ukończyć ten krok, musisz mieć połączenie z Internetem. 

Otwórz wiersz polecenia, przejdź do katalogu, do którego pobrano program inicjujący, i Użyj parametrów programu inicjującego, zgodnie z definicją w [parametrach wiersza polecenia Użyj, aby zainstalować stronę programu Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) , aby utworzyć i zachować pamięć podręczną instalacji sieci. Typowe przykłady tworzenia układów początkowych przedstawiono poniżej i w [przykładach parametrów wiersza polecenia do instalacji programu Visual Studio](../install/command-line-parameter-examples.md).  

   > [!IMPORTANT]
   > Pełny układ początkowy dla jednego języka regionalnego wymaga około 35 GB miejsca na dysku dla programu Visual Studio Community i 42 GB na Visual Studio Enterprise. Dodatkowe [Ustawienia regionalne języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) wymagają około połowy GB każdego z nich. Aby uzyskać więcej informacji, zobacz sekcję [Dostosowywanie układu sieciowego](#customize-the-network-layout) . Należy mieć na uwadze, że kolejne aktualizacje układu również muszą być przechowywane w tej samej lokalizacji sieciowej, dlatego należy się spodziewać, że zawartość katalogu w lokalizacji układu sieciowego może być dość duża w czasie.  
   
- Aby utworzyć początkowy układ Visual Studio Enterprise ze wszystkimi językami i wszystkimi funkcjami, uruchom polecenie:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Aby utworzyć początkowy układ Visual Studio Professional ze wszystkimi językami i wszystkimi funkcjami, uruchom polecenie:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Modyfikuj response.jsw pliku

Można zmodyfikować plik, `response.json` Aby ustawić wartości domyślne, które są używane podczas uruchamiania Instalatora.  Na przykład można skonfigurować `response.json` plik do wybierania określonego zestawu obciążeń, które powinny być wybierane automatycznie. Można również skonfigurować, `response.json` Aby określić, czy klient ma otrzymywać tylko zaktualizowane pliki z lokalizacji układu sieciowego. Aby uzyskać więcej informacji, zobacz [Automatyzowanie instalacji programu Visual Studio przy użyciu pliku odpowiedzi](../install/automated-installation-with-response-file.md). 

Jeśli napotkasz problem z programem inicjującym programu Visual Studio, który zgłasza błąd podczas parowania z `response.json` plikiem, zobacz [Rozwiązywanie problemów związanych z siecią podczas instalowania lub używania strony programu Visual Studio](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) , aby uzyskać więcej informacji.

## <a name="copy-the-layout-to-a-network-share"></a>Kopiuj układ do udziału sieciowego

Hostowanie układu w udziale sieciowym, aby można go było uruchomić z poziomu komputerów klienckich.

Poniższy przykład używa [xcopy](/windows-server/administration/windows-commands/xcopy/). W razie potrzeby można również użyć [Robocopy](/windows-server/administration/windows-commands/robocopy/).

::: moniker range="vs-2017"

Przykład:

```cmd
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> Aby zapobiec wystąpieniu błędu, upewnij się, że pełna ścieżka układu jest krótsza niż 80 znaków.

## <a name="customize-the-network-layout"></a>Dostosuj układ sieci

Istnieje kilka opcji, których można użyć, aby dostosować układ sieci. Można utworzyć układ częściowy, który zawiera tylko określony zestaw [ustawień regionalnych języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [obciążeń, składników i ich zalecanych lub opcjonalnych zależności](workload-and-component-ids.md). Może to być przydatne, Jeśli wiesz, że zamierzasz wdrożyć tylko podzestaw obciążeń na stacjach roboczych klientów. Typowe parametry wiersza polecenia służące do dostosowywania układu obejmują:

* `--add` Aby określić [obciążenie lub identyfikatory składników](workload-and-component-ids.md). <br>Jeśli `--add` jest używany, pobierane są tylko te obciążenia i składniki określone z `--add` .  Jeśli `--add` nie jest używany, wszystkie obciążenia i składniki są pobierane.
* `--includeRecommended` Aby uwzględnić wszystkie zalecane składniki dla określonych identyfikatorów obciążeń
* `--includeOptional` w celu uwzględnienia wszystkich zalecanych i opcjonalnych składników dla określonych identyfikatorów obciążeń.
* `--lang` Aby określić [Ustawienia regionalne języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Poniżej przedstawiono kilka przykładów tworzenia niestandardowego układu częściowego.

* Aby pobrać wszystkie obciążenia i składniki tylko dla jednego języka, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Aby pobrać wszystkie obciążenia i składniki dla wielu języków, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Aby pobrać jedno obciążenie dla wszystkich języków, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Aby pobrać dwa obciążenia i jeden opcjonalny składnik dla trzech języków, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Aby pobrać dwa obciążenia i wszystkie zalecane składniki:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Aby pobrać dwa obciążenia i wszystkie zalecane i opcjonalne składniki, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

### <a name="save-your-layout-options"></a>Zapisz opcje układu

Po uruchomieniu polecenia układu, określone opcje są zapisywane (takie jak obciążenia i języki). Kolejne polecenia układu będą obejmować wszystkie poprzednie opcje.  Oto przykład układu z jednym obciążeniem tylko dla języka angielskiego:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Aby zaktualizować ten układ do nowszej wersji, nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia są zapisywane i używane przez dowolne kolejne polecenia układu w tym folderze układu.  Następujące polecenie zaktualizuje istniejący układ częściowy.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Jeśli chcesz dodać dodatkowe obciążenie, poniżej przedstawiono przykład sposobu, w jaki należy to zrobić. W takim przypadku dodamy obciążenie platformy Azure i zlokalizowany język.  W tym układzie uwzględniono teraz zarówno program Managed Desktop, jak i platformę Azure.  Zasoby językowe w języku angielskim i niemieckim są dołączone do wszystkich tych obciążeń. Układ został zaktualizowany do najnowszej dostępnej wersji.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Jeśli chcesz zaktualizować istniejący układ do pełnego układu, użyj opcji--all, jak pokazano w poniższym przykładzie.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Wdrażanie z poziomu instalacji sieciowej

Administratorzy mogą wdrażać program Visual Studio na stacjach roboczych klienta jako część skryptu instalacji. Lub Użytkownicy, którzy mają uprawnienia administratora, mogą uruchomić Instalatora bezpośrednio z udziału, aby zainstalować program Visual Studio na swoich komputerach.

* Użytkownicy mogą zainstalować program, uruchamiając następujące polecenie: <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Administratorzy mogą zainstalować w trybie nienadzorowanym, uruchamiając następujące polecenie:

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Aby zapobiec wystąpieniu błędu, upewnij się, że pełna ścieżka układu jest krótsza niż 80 znaków.

> [!TIP]
> W przypadku wykonywania jako część pliku wsadowego, `--wait` Opcja zapewnia, że `vs_enterprise.exe` proces czeka na zakończenie instalacji, zanim zwróci kod zakończenia.
>
> Jest to przydatne, jeśli administrator przedsiębiorstwa chce wykonać dalsze działania w ramach ukończonej instalacji (na przykład w celu [zastosowania klucza produktu do pomyślnej instalacji](automatically-apply-product-keys-when-deploying-visual-studio.md)), ale musi poczekać na zakończenie instalacji, aby obsłużyć kod powrotny z tej instalacji.
>
> Jeśli nie używasz `--wait` , `vs_enterprise.exe` proces kończy się przed ukończeniem instalacji i zwróci niedokładny kod zakończenia, który nie reprezentuje stanu operacji instalacji.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> W przypadku instalacji w trybie offline, jeśli zostanie wyświetlony komunikat o błędzie "nie można odnaleźć produktu zgodnego z następującymi parametrami", upewnij się, że używasz `--noweb` przełącznika z wersją 16.3.5 lub nowszą.
>
::: moniker-end

Podczas instalacji z układu, zainstalowaną zawartość uzyskuje się z układu. Jednak w przypadku wybrania składnika, który nie jest w układzie, zostanie on pobrany z Internetu.  Aby uniemożliwić pobranie przez Instalatora programu Visual Studio żadnej zawartości, której brakuje w układzie, użyj `--noWeb` opcji. Jeśli `--noWeb` jest używany, a układ nie zawiera żadnej zawartości wybranej do zainstalowania, instalacja zakończy się niepowodzeniem.

> [!TIP]
> Jeśli chcesz zainstalować ze źródła offline na komputerze niepołączonym z Internetem, określ `--noWeb` `--noUpdateInstaller` Opcje i. Dotychczas uniemożliwia pobieranie zaktualizowanych obciążeń, składników i tak dalej. Ten ostatni uniemożliwia Instalatorowi samodzielne aktualizowanie z sieci Web.

> [!IMPORTANT]
> `--noWeb`Opcja nie zatrzymuje instalacji programu Visual Studio na komputerze połączonym z Internetem, sprawdzając aktualizacje. Aby uzyskać więcej informacji, zobacz stronę [sterowanie aktualizacjami w przypadku sieci opartych na programie Visual Studio](controlling-updates-to-visual-studio-deployments.md) .

### <a name="error-codes"></a>Kody błędów

Jeśli użyto `--wait` parametru, a następnie w zależności od wyniku operacji, `%ERRORLEVEL%` zmienna środowiskowa jest ustawiona na jedną z następujących wartości:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Aktualizowanie układu instalacji sieciowej

Gdy aktualizacje produktów staną się dostępne, warto [zaktualizować układ instalacji sieci](update-a-network-installation-of-visual-studio.md) w celu uwzględnienia zaktualizowanych pakietów.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Jak utworzyć układ poprzedniej wersji programu Visual Studio

Najpierw należy zrozumieć, że istnieją dwa typy programu inicjującego programu Visual Studio — jeden, który może być scharakteryzowany przez słowa "Najnowsza", "Current", "Evergreen" i "Tip", co oznacza, że jest to "stała wersja". Oba typy plików programu inicjującego mają dokładnie taką samą nazwę, a najlepszym sposobem odróżnienia typu jest zwrócenie uwagi do lokalizacji, z której pochodzi. Program inicjujący programu Visual Studio dostępny na [stronie pliki do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) jest traktowany jako Evergreen program inicjujący Visual Studio i zawsze instalują (lub aktualizują) najnowszą wersję, która jest dostępna w kanale w momencie uruchomienia programu inicjującego. Program inicjujący programu Visual Studio dostępny na stronie [wydań programu Visual studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history) lub osadzony w ramach aktualizacji administratora w wykazie Microsoft Update instalują określoną stałą wersję produktu. 

Tak więc, jeśli pobierzesz program inicjujący Evergreen programu Visual Studio już dziś i uruchomisz od razu sześć miesięcy, zainstaluje wersję programu Visual Studio, która jest aktualna w chwili uruchomienia programu inicjującego. Zaprojektowano, aby zawsze instalować najnowsze bity i zachować aktualność.

Jeśli zostanie pobrany program inicjujący stałe łącze lub zostanie uruchomiona aktualizacja administratora pobrana z wykazu Microsoft, wówczas zawsze zostanie zainstalowana określona wersja produktu bez względu na to, kiedy została uruchomiona.

Na koniec można utworzyć układ sieci przy użyciu dowolnego z tych programów inicjujących, a wersja, która zostanie utworzona w układzie, zależy od używanego programu inicjującego, na przykład jego wersja stała lub bieżąca. Następnie można zaktualizować układ sieci przy użyciu dowolnego późniejszego programu inicjującego lub można również użyć pakietu aktualizacji administratora z wykazu Microsoft Update. Bez względu na sposób aktualizowania układu, wynikający ze zaktualizowanego układu będzie pamięć podręczna pakietu, która zawiera określoną wersję produktu, a następnie będzie zachowywać się jak stały program inicjujący link. Tak więc, za każdym razem, gdy klient zostanie zainstalowany z układu, klient zainstaluje określoną wersję programu Visual Studio, która istnieje w układzie (mimo że nowsza wersja może istnieć w trybie online). 

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak uzyskać pomoc techniczną dla Instalatora w trybie offline

Jeśli wystąpi problem z instalacją w trybie offline, chcemy wiedzieć o tym. Najlepszym sposobem na poinformowanie nas jest użycie narzędzia [Zgłoś problem](../ide/how-to-report-a-problem-with-visual-studio.md) . Korzystając z tego narzędzia, możesz wysłać nam dane telemetryczne i dzienniki, które muszą pomóc nam w zdiagnozowaniu i rozwiązaniu problemu.

Oferujemy również opcję pomocy technicznej dotyczącej [**rozmowy z instalacją**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) dla problemów związanych z instalacją.

Dostępne są również inne opcje pomocy technicznej. Listę można znaleźć na naszej stronie [opinii](../ide/feedback-options.md) .

## <a name="see-also"></a>Zobacz też

- [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
- [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Rozwiązywanie problemów związanych z siecią podczas instalowania programu Visual Studio lub korzystania z niego](troubleshooting-network-related-errors-in-visual-studio.md)
- [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
- [Cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
- [Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi](update-servicing-baseline.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
- [Zainstaluj certyfikaty wymagane do instalacji w trybie offline programu Visual Studio](install-certificates-for-visual-studio-offline.md)
