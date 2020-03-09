---
title: Utworzenie instalacji sieciowej
description: Dowiedz się, jak utworzyć punkt instalacji sieciowej dla wdrażania programu Visual Studio w przedsiębiorstwie.
ms.date: 10/29/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bc31b6c5286e5d02d5fd6d4da441a001f190de90
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410106"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Tworzenie instalacji sieciowej programu Visual Studio

Zazwyczaj administrator przedsiębiorstwa tworzy punkt instalacji sieci do wdrożenia na stacjach roboczych klienta. Zaprojektowano program Visual Studio, aby umożliwić buforowanie plików dla początkowej instalacji wraz ze wszystkimi aktualizacjami produktów w jednym folderze. (Ten proces jest również określany jako _Tworzenie układu_).

Firma Microsoft wykonane to dlatego, że stacje robocze klienta można użyć tej samej lokalizacji sieci do zarządzania ich instalacji, nawet jeśli ich jeszcze nie zostało zaktualizowane do obsługi najnowszej aktualizacji.

 > [!NOTE]
 > Jeśli masz wiele wersji programu Visual Studio używane w przedsiębiorstwie (na przykład program Visual Studio Professional i Visual Studio Enterprise), należy utworzyć udział instalacji oddzielnej sieci dla każdej wersji.

## <a name="download-the-visual-studio-bootstrapper"></a>Pobierz program inicjujący programu Visual Studio

Pobierz plik programu inicjującego dla używanej wersji programu Visual Studio. Upewnij się, że wybrano pozycję **Zapisz**, a następnie wybierz pozycję **Otwórz folder**.

::: moniker range="vs-2017"

Aby uzyskać program inicjujący dla programu Visual Studio 2017, zobacz stronę pobierania [poprzednich wersji programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) , aby uzyskać szczegółowe informacje o tym, jak to zrobić.

Plik wykonywalny instalatora&mdash;lub być bardziej specyficzny,&mdash;pliku programu inicjującego powinien być zgodny z jedną z następujących czynności:

| Wersja | Nazwa pliku |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise. exe** |
|Visual Studio Professional | **vs_professional. exe** |
|Visual Studio Build Tools   | **vs_buildtools. exe** |

Inne obsługiwane programu inicjujące obejmują **vs_feedbackclient. exe**, **vs_TeamExplorer. exe**, **vs_testagent. exe**, **vs_testcontroller. exe**i **vs_testprofessional. exe**.

::: moniker-end

::: moniker range="vs-2019"

Plik wykonywalny instalatora&mdash;lub być bardziej specyficzny,&mdash;pliku programu inicjującego powinien być zgodny z jedną z następujących czynności:

|Wersja | Pobieranie|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise. exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional. exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools. exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Inne obsługiwane programu inicjujące obejmują [vs_TeamExplorer. exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent. exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)i [vs_testcontroller. exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

>[!TIP]
>Jeśli wcześniej pobrano plik inicjujący i chcesz sprawdzić jego wersję, poniżej przedstawiono sposób. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inicjującego, wybierz polecenie **Właściwości**, wybierz kartę **szczegóły** , a następnie Wyświetl numer **wersji produktu** . Aby dopasować tę liczbę do wersji programu Visual Studio, zobacz stronę [numery kompilacji i daty wydania programu Visual Studio](visual-studio-build-numbers-and-release-dates.md) .

## <a name="create-an-offline-installation-folder"></a>Utwórz folder instalacji w trybie offline

Musi mieć połączenie internetowe, aby ukończyć ten krok. Aby utworzyć instalację w trybie offline ze wszystkimi językami i wszystkimi funkcjami, użyj polecenia, które jest podobne do jednego z poniższych przykładów.

   > [!IMPORTANT]
   > Pełny układ programu Visual Studio wymaga co najmniej 35 GB miejsca na dysku, co może potrwać trochę czasu. Zobacz sekcję [Dostosowywanie układu sieciowego](#customize-the-network-layout) , aby uzyskać szczegółowe informacje na temat sposobu tworzenia układu z tylko składnikami, które chcesz zainstalować.
   >
   > [!TIP]
   > Upewnij się, uruchom polecenie z katalogu pobierania. Zwykle jest to `C:\Users\<username>\Downloads` na komputerze z systemem Windows 10.

- For Visual Studio Enterprise, run:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Dla programu Visual Studio Professional Uruchom polecenie:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Zmodyfikuj plik response.json

Można zmodyfikować response.json, aby ustawić wartości domyślne, które są używane po uruchomieniu Instalatora.  Na przykład można skonfigurować plik `response.json`, aby wybrać określony zestaw obciążeń automatycznie. Aby uzyskać szczegółowe informacje [, zobacz Automatyzowanie instalacji programu Visual Studio z plikiem odpowiedzi](automated-installation-with-response-file.md) .

W przypadku wystąpienia problemu z programem inicjującym programu Visual Studio, który zgłasza błąd podczas parowania z plikiem Response. JSON, zobacz sekcję "nie można przeanalizować identyfikatora z procesu nadrzędnego" w temacie [Rozwiązywanie problemów związanych z siecią podczas instalowania lub używania strony programu Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) , aby uzyskać więcej informacji na temat tego, co należy zrobić.

## <a name="copy-the-layout-to-a-network-share"></a>Skopiować układ do udziału sieciowego

Hosta układu w udziale sieciowym, dzięki czemu może działać z innych komputerów.

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

Istnieje kilka opcji, których można użyć w celu dostosowania układu sieci. Można utworzyć układ częściowy, który zawiera tylko określony zestaw [ustawień regionalnych języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [obciążeń, składników i ich zalecanych lub opcjonalnych zależności](workload-and-component-ids.md). Może to być przydatne, Jeśli wiesz, że zamierzasz wdrożyć tylko podzestaw obciążeń na stacjach roboczych klientów. Typowe parametry wiersza polecenia dla dostosowywania układu obejmują:

* `--add` określić [obciążenia lub identyfikatory składników](workload-and-component-ids.md). <br>Jeśli zostanie użyta `--add`, pobierane są tylko te obciążenia i składniki określone z `--add`.  Jeśli `--add` nie jest używany, wszystkie obciążenia i składniki zostaną pobrane.
* `--includeRecommended`, aby uwzględnić wszystkie zalecane składniki dla określonych identyfikatorów obciążeń
* `--includeOptional`, aby uwzględnić wszystkie zalecane i opcjonalne składniki dla określonych identyfikatorów obciążeń.
* `--lang`, aby określić [Ustawienia regionalne języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Poniżej przedstawiono kilka przykładów sposobu tworzenia niestandardowego układu częściowe.

* Aby pobrać wszystkie obciążenia i składniki dla tylko jednego języka, uruchom polecenie:

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

* Aby pobrać dwóch obciążeń i jeden składnik opcjonalny w trzech językach, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Aby pobrać dwa obciążenia i wszystkie zalecane składniki:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Aby pobrać dwóch obciążeń i wszystkie ich zalecanych i opcjonalnych składników, uruchom polecenie:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Nowość w wersji 15,3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Zapisz opcje układu

::: moniker-end

Po uruchomieniu polecenia układ, opcje, które określisz są zapisywane (na przykład obciążeń i języków). Układ kolejnych poleceń będzie zawierać wszystkie poprzednie opcje.  Poniżej przedstawiono przykład układu z jednego obciążeniem dla języka angielskiego tylko:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Jeśli chcesz zaktualizować ten układ do nowszej wersji, nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia są zapisywane i używane przez dowolne polecenia kolejnych układu, w tym folderze układu.  Następujące polecenie spowoduje zaktualizowanie istniejących układ częściowe.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Jeśli chcesz dodać dodatkowe obciążenia, tutaj przykładowy sposób to zrobić. W tym przypadku dodamy obciążenie platformy Azure i zlokalizowanego języka.  Teraz zarządzane pulpitu i platformy Azure znajdują się w tym układzie.  Zasoby językowe w języku angielskim i niemieckim są dołączone do wszystkich tych obciążeń. Układ jest aktualizowane do najnowszej dostępnej wersji.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Aby zaktualizować istniejący układ pełny układ, należy użyć wszystkich opcji, jak pokazano w poniższym przykładzie.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Wdrażanie z poziomu instalacji sieciowej

Administratorzy mogą wdrożyć Visual Studio na klienckich stacjach roboczych w skrypcie instalacji. Lub użytkowników, którzy mają uprawnienia administratora, można uruchomić Instalatora bezpośrednio z poziomu udziału, aby zainstalować program Visual Studio na swojej maszynie.

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
> Podczas wykonywania jako część pliku wsadowego, opcja `--wait` zapewnia, że proces `vs_enterprise.exe` czeka na zakończenie instalacji, zanim zwróci kod zakończenia.
>
> Jest to przydatne, jeśli administrator przedsiębiorstwa chce wykonać dalsze działania w ramach ukończonej instalacji (na przykład w celu [zastosowania klucza produktu do pomyślnej instalacji](automatically-apply-product-keys-when-deploying-visual-studio.md)), ale musi poczekać na zakończenie instalacji, aby obsłużyć kod powrotny z tej instalacji.
>
> Jeśli nie używasz `--wait`, proces `vs_enterprise.exe` zostanie zakończony przed ukończeniem instalacji i zwróci niewłaściwy kod zakończenia, który nie reprezentuje stanu operacji instalacji.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> W przypadku instalacji w trybie offline, jeśli zostanie wyświetlony komunikat o błędzie "nie można odnaleźć produktu zgodnego z następującymi parametrami", upewnij się, że używasz przełącznika `--noweb` w wersji 16.3.5 lub nowszej.
>
::: moniker-end

Podczas instalacji z układu, zawartość, która jest zainstalowana jest uzyskiwany z układu. Jednak w przypadku wybrania składnika, który nie jest w układzie, zostanie on pobrany z Internetu.  Aby uniemożliwić pobranie przez Instalatora programu Visual Studio żadnej zawartości, której brakuje w układzie, użyj opcji `--noWeb`. Jeśli `--noWeb` jest używany, a układ nie zawiera żadnej zawartości wybranej do zainstalowania, instalacja zakończy się niepowodzeniem.

> [!IMPORTANT]
> Opcja `--noWeb` nie zatrzymuje sprawdzania dostępności aktualizacji przez Instalatora programu Visual Studio. Aby uzyskać więcej informacji, zobacz stronę [sterowanie aktualizacjami w przypadku sieci opartych na programie Visual Studio](controlling-updates-to-visual-studio-deployments.md) .

### <a name="error-codes"></a>Kody błędów

Jeśli użyto `--wait` parametru, a następnie w zależności od wyniku operacji, zmienna środowiskowa `%ERRORLEVEL%` jest ustawiana na jedną z następujących wartości:

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
> Jeśli jednak utworzysz *Układ* , a następnie zainstalujesz go, układ instaluje określoną wersję programu Visual Studio, która istnieje w układzie. Mimo że nowszej wersji może istnieć w trybie online, otrzymasz wersji programu Visual Studio, który jest w układzie.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Program inicjujący programu Visual Studio, który jest dostępny w systemie [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads) , pobiera i instalują najnowszą wersję programu Visual Studio, która jest dostępna przy każdym uruchomieniu.
>
> Dlatego w przypadku pobrania programu *inicjującego* program Visual Studio już dziś i uruchomienia przez niego sześciu miesięcy od teraz zostanie zainstalowana wersja programu Visual Studio, która jest aktualna w czasie uruchamiania programu inicjującego.
>
> Jeśli jednak utworzysz *Układ* , a następnie zainstalujesz go, układ instaluje określoną wersję programu Visual Studio, która istnieje w układzie. Mimo że nowszej wersji może istnieć w trybie online, otrzymasz wersji programu Visual Studio, który jest w układzie.

::: moniker-end

Jeśli musisz utworzyć układ dla starszej wersji programu Visual Studio, przejdź do [https://my.visualstudio.com](https://my.visualstudio.com) , aby pobrać "Fixed" wersje programu inicjującego Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak uzyskać pomoc techniczną dla Instalatora w trybie offline

Jeśli wystąpi problem z instalacją w trybie offline, chcielibyśmy się dowiedzieć o nim. Najlepszym sposobem na poinformowanie nas jest użycie narzędzia [Zgłoś problem](../ide/how-to-report-a-problem-with-visual-studio.md) . Korzystając z tego narzędzia, możesz wysłać nam telemetrii i dzienniki, musimy pomóc nam zdiagnozować i rozwiązać problem.

Oferujemy również opcję obsługi [**rozmowy na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) dla problemów związanych z instalacją.

Inne opcje pomocy technicznej dostępne, mamy zbyt. Listę można znaleźć na naszej stronie [opinii](../ide/feedback-options.md) .

## <a name="see-also"></a>Zobacz także

- [Przewodnik administratora programu Visual Studio](visual-studio-administrator-guide.md)
- [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Rozwiązywanie problemów związanych z siecią podczas instalowania programu Visual Studio lub korzystania z niego](troubleshooting-network-related-errors-in-visual-studio.md)
- [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
- [Cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
- [Aktualizowanie programu Visual Studio w punkcie odniesienia obsługi](update-servicing-baseline.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
