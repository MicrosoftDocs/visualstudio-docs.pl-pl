---
title: Tworzenie instalacji sieciowej
description: Dowiedz się, jak utworzyć punkt instalacji sieci na potrzeby wdrażania programu Visual Studio w ramach przedsiębiorstwa.
ms.date: 08/27/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b572a6854d505704accd79cc4da2ac4e52c193d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850178"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Tworzenie instalacji sieciowej programu Visual Studio

Zazwyczaj administrator przedsiębiorstwa tworzy punkt instalacji sieci do wdrożenia na stacjach roboczych klienta. Zaprojektowano program Visual Studio, aby umożliwić buforowanie plików dla początkowej instalacji wraz ze wszystkimi aktualizacjami produktów w jednym folderze. (Ten proces jest również określany jako _Tworzenie układu_).

Zostało to zrobione, tak że stacje robocze klientów mogą używać tej samej lokalizacji sieciowej do zarządzania instalacją, nawet jeśli nie zostały jeszcze zaktualizowane do najnowszej aktualizacji obsługi.

 > [!NOTE]
 > Jeśli masz wiele wydań programu Visual Studio używanych w przedsiębiorstwie (na przykład zarówno Visual Studio Professional i Visual Studio Enterprise), musisz utworzyć osobny udział instalacji sieci dla każdej wersji.

## <a name="download-the-visual-studio-bootstrapper"></a>Pobieranie programu inicjującego programu Visual Studio

Pobierz plik programu inicjującego dla używanej wersji programu Visual Studio. Upewnij się, że wybrano pozycję **Zapisz**, a następnie wybierz pozycję **Otwórz folder**.

::: moniker range="vs-2017"

Aby uzyskać program inicjujący dla programu Visual Studio 2017, zobacz stronę pobierania [poprzednich wersji programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) , aby uzyskać szczegółowe informacje o tym, jak to zrobić.

Plik wykonywalny instalatora &mdash; lub bardziej szczegółowy, musi być zgodny z plikiem programu inicjującego &mdash; lub być podobny do jednego z poniższych.

| Wersja | Nazwa pliku |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Build Tools   | **vs_buildtools.exe** |

Inne obsługiwane programu inicjujące obejmują **vs_feedbackclient.exe**, **vs_teamexplorer.exe**, **vs_testagent.exe**, **vs_testcontroller.exe** i **vs_testprofessional.exe**.

::: moniker-end

::: moniker range="vs-2019"

Plik wykonywalny instalatora &mdash; lub bardziej szczegółowy, musi być zgodny z plikiem programu inicjującego &mdash; lub być podobny do jednego z poniższych.

|Wersja | Pobierz|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Inne obsługiwane programu inicjujące obejmują [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)i [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

>[!TIP]
>Jeśli wcześniej pobrano plik inicjujący i chcesz sprawdzić jego wersję, poniżej przedstawiono sposób. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inicjującego, wybierz polecenie **Właściwości**, wybierz kartę **szczegóły** , a następnie Wyświetl numer **wersji produktu** . Aby dopasować tę liczbę do wersji programu Visual Studio, zobacz stronę [numery kompilacji i daty wydania programu Visual Studio](visual-studio-build-numbers-and-release-dates.md) .

## <a name="create-an-offline-installation-folder"></a>Tworzenie folderu instalacyjnego w trybie offline

Aby ukończyć ten krok, musisz mieć połączenie z Internetem. Aby utworzyć instalację w trybie offline ze wszystkimi językami i wszystkimi funkcjami, użyj polecenia, które jest podobne do jednego z poniższych przykładów.

   > [!IMPORTANT]
   > Pełny układ ustawień regionalnych dla jednego języka wymaga około 35 GB miejsca na dysku dla programu Visual Studio Community i 42 GB na Visual Studio Enterprise. Dodatkowe [Ustawienia regionalne języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) wymagają około połowy GB każdego z nich. Aby uzyskać więcej informacji, zobacz sekcję [Dostosowywanie układu sieciowego](#customize-the-network-layout) .
   >
   > [!TIP]
   > Upewnij się, że uruchamiasz polecenie z katalogu pobierania. Zwykle jest to `C:\Users\<username>\Downloads` na komputerze z systemem Windows 10.

- W przypadku Visual Studio Enterprise Uruchom polecenie:

  ```vs_enterprise.exe --layout c:\VSLayout```

- W przypadku Visual Studio Professional Uruchom polecenie:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Modyfikuj response.jsw pliku

response.jsmożna modyfikować, aby ustawić wartości domyślne, które są używane podczas uruchamiania Instalatora.  Na przykład można skonfigurować `response.json` plik, aby wybrać określony zestaw obciążeń automatycznie. Aby uzyskać szczegółowe informacje [, zobacz Automatyzowanie instalacji programu Visual Studio z plikiem odpowiedzi](automated-installation-with-response-file.md) .

W przypadku wystąpienia problemu z programem inicjującym programu Visual Studio, który zgłasza błąd podczas parowania z response.jsem pliku, zobacz sekcję "nie można przeanalizować identyfikatora z procesu nadrzędnego" w temacie [Rozwiązywanie problemów związanych z siecią podczas instalowania lub używania strony programu Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) , aby uzyskać więcej informacji na temat tego, co należy zrobić.

## <a name="copy-the-layout-to-a-network-share"></a>Kopiuj układ do udziału sieciowego

Hostowanie układu w udziale sieciowym, aby można go było uruchomić z innych komputerów.

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

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Nowość w wersji 15,3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Zapisz opcje układu

::: moniker-end

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

::: moniker range="vs-2017"

> [!NOTE]
> Program inicjujący programu Visual Studio, który jest dostępny w systemie [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) , pobiera i instalują najnowszą wersję programu Visual Studio, która jest dostępna przy każdym uruchomieniu.
>
> Dlatego w przypadku pobrania programu *inicjującego* program Visual Studio już dziś i uruchomienia przez niego sześciu miesięcy od teraz zostanie zainstalowana wersja programu Visual Studio, która jest aktualna w czasie uruchamiania programu inicjującego.
>
> Jeśli jednak utworzysz *Układ* , a następnie zainstalujesz go, układ instaluje określoną wersję programu Visual Studio, która istnieje w układzie. Mimo że nowsza wersja może istnieć w trybie online, uzyskasz wersję programu Visual Studio, która jest w układzie.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Program inicjujący programu Visual Studio, który jest dostępny w systemie [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads) , pobiera i instalują najnowszą wersję programu Visual Studio, która jest dostępna przy każdym uruchomieniu.
>
> Dlatego w przypadku pobrania programu *inicjującego* program Visual Studio już dziś i uruchomienia przez niego sześciu miesięcy od teraz zostanie zainstalowana wersja programu Visual Studio, która jest aktualna w czasie uruchamiania programu inicjującego.
>
> Jeśli jednak utworzysz *Układ* , a następnie zainstalujesz go, układ instaluje określoną wersję programu Visual Studio, która istnieje w układzie. Mimo że nowsza wersja może istnieć w trybie online, uzyskasz wersję programu Visual Studio, która jest w układzie.

::: moniker-end

Jeśli musisz utworzyć układ dla starszej wersji programu Visual Studio, przejdź do [https://my.visualstudio.com](https://my.visualstudio.com) strony, aby pobrać "naprawione" wersje programu inicjującego Visual Studio.

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