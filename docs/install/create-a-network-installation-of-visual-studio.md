---
title: Tworzenie instalacji sieciowej
description: Dowiedz się, jak utworzyć punkt instalacji sieciowej do wdrażania programu Visual Studio w przedsiębiorstwie.
ms.date: 03/27/2020
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
ms.openlocfilehash: ea7efd82aa25844e8eb33745aa53d44be1ed14f6
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80544063"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Tworzenie instalacji sieciowej programu Visual Studio

Zazwyczaj administrator przedsiębiorstwa tworzy punkt instalacji sieciowej do wdrożenia na klienckich stacjach roboczych. Zaprojektowaliśmy program Visual Studio, aby umożliwić buforowanie plików dla instalacji początkowej wraz ze wszystkimi aktualizacjami produktu do jednego folderu. (Ten proces jest również określany jako _tworzenie układu_.)

Zrobiliśmy to, aby klienckie stacje robocze mogły używać tej samej lokalizacji sieciowej do zarządzania instalacją, nawet jeśli nie zostały jeszcze zaktualizowane do najnowszej aktualizacji obsługi.

 > [!NOTE]
 > Jeśli w przedsiębiorstwie jest dostępnych wiele wersji programu Visual Studio (na przykład zarówno visual studio professional, jak i visual studio enterprise), należy utworzyć oddzielny udział instalacji sieciowej dla każdej wersji.

## <a name="download-the-visual-studio-bootstrapper"></a>Pobieranie programu iniekcjowego programu Visual Studio

Pobierz plik programu bootstrapper dla żądanej wersji programu Visual Studio. Upewnij się, że wybierz pozycję **Zapisz**, a następnie wybierz pozycję **Otwórz folder**.

::: moniker range="vs-2017"

Aby uzyskać program uruchamiany dla programu Visual Studio 2017, zobacz stronę pobierania [poprzednich wersji programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/) aby uzyskać szczegółowe informacje na ten temat.

Plik wykonywalny konfiguracji lub bardziej&mdash;&mdash;szczegółowy plik programu inichowania powinien być zgodny lub podobny do jednego z poniższych.

| Wersja | Pod nazwą |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Build Tools   | **vs_buildtools.exe** |

Inne obsługiwane programy inauacyjno-inieksowe to **vs_feedbackclient.exe**, **vs_teamexplorer.exe**, **vs_testagent.exe**, **vs_testcontroller.exe**i **vs_testprofessional.exe**.

::: moniker-end

::: moniker range="vs-2019"

Plik wykonywalny konfiguracji lub bardziej&mdash;&mdash;szczegółowy plik programu inichowania powinien być zgodny lub podobny do jednego z poniższych.

|Wersja | Pobierz|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Inne obsługiwane programy inauacyjno-inieksowe to [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)i [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

>[!TIP]
>Jeśli wcześniej pobrano plik boottrappera i chcesz zweryfikować jego wersję, oto jak to zrobić. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inikuscyjny, wybierz polecenie **Właściwości**, wybierz kartę **Szczegóły,** a następnie wyświetl numer **wersji produktu.** Aby dopasować tę liczbę do wersji programu Visual Studio, zobacz [numery kompilacji programu Visual Studio i daty wydania](visual-studio-build-numbers-and-release-dates.md) strony.

## <a name="create-an-offline-installation-folder"></a>Tworzenie folderu instalacyjnego trybu offline

Aby wykonać ten krok, musisz mieć połączenie z Internetem. Aby utworzyć instalację w trybie offline ze wszystkimi językami i wszystkimi funkcjami, należy użyć polecenia podobnego do jednego z poniższych przykładów.

   > [!IMPORTANT]
   > Kompletny układ programu Visual Studio wymaga co najmniej 35 GB miejsca na dysku i może zająć trochę czasu, aby pobrać. Zobacz [sekcję Dostosowywanie układu sieci,](#customize-the-network-layout) aby uzyskać szczegółowe informacje na temat tworzenia układu tylko ze składnikami, które chcesz zainstalować.
   >
   > [!TIP]
   > Upewnij się, że polecenie zostało uruchomione z katalogu Pobierania. Zazwyczaj jest `C:\Users\<username>\Downloads` to na komputerze z systemem Windows 10.

- W programie Visual Studio Enterprise uruchom:

  ```vs_enterprise.exe --layout c:\VSLayout```

- W programie Visual Studio Professional uruchom:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Modyfikowanie pliku response.json

Można zmodyfikować response.json, aby ustawić wartości domyślne, które są używane podczas uruchamiania konfiguracji.  Na przykład można skonfigurować `response.json` plik tak, aby automatycznie wybierał określony zestaw obciążeń. Zobacz [automatyzacji instalacji programu Visual Studio z plikiem odpowiedzi,](automated-installation-with-response-file.md) aby uzyskać szczegółowe informacje.

I jeśli napotkasz problem z programem Visual Studio boottrapper zrzucając błąd podczas parowania go z pliku response.json, zobacz "Nie można przeanalizować identyfikator z procesu nadrzędnego" sekcji [Rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania lub korzystania ze](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) strony programu Visual Studio, aby uzyskać więcej informacji na temat tego, co należy zrobić.

## <a name="copy-the-layout-to-a-network-share"></a>Kopiowanie układu do udziału sieciowego

Hostuj układ w udziale sieciowym, aby można go było uruchomić z innych komputerów.

W poniższym przykładzie użyto [xcopy](/windows-server/administration/windows-commands/xcopy/). Możesz również użyć [roboboskopii](/windows-server/administration/windows-commands/robocopy/), jeśli chcesz.  

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
> Aby zapobiec błędowi, upewnij się, że ścieżka pełnego układu jest mniejsza niż 80 znaków.

## <a name="customize-the-network-layout"></a>Dostosowywanie układu sieci

Istnieje kilka opcji, których można użyć do dostosowania układu sieci. Można utworzyć układ częściowy, który zawiera tylko określony zestaw [ustawień regionalnych języka,](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) [obciążeń, składników i ich zalecanych lub opcjonalnych zależności.](workload-and-component-ids.md) Może to być przydatne, jeśli wiesz, że zamierzasz wdrożyć tylko podzbiór obciążeń na stacjach roboczych klienta. Typowe parametry wiersza polecenia do dostosowywania układu obejmują:

* `--add`, aby określić [identyfikatory obciążenia lub komponentu](workload-and-component-ids.md). <br>Jeśli `--add` jest używany, pobierane są `--add` tylko te obciążenia i składniki określone za pomocą.  Jeśli `--add` nie jest używany, wszystkie obciążenia i składniki są pobierane.
* `--includeRecommended`, aby uwzględnić wszystkie zalecane składniki dla określonych identyfikatorów obciążenia
* `--includeOptional`, aby uwzględnić wszystkie zalecane i opcjonalne składniki dla określonych identyfikatorów obciążenia.
* `--lang`, aby określić [ustawienia regionalne języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Oto kilka przykładów tworzenia niestandardowego układu częściowego.

* Aby pobrać wszystkie obciążenia i składniki tylko dla jednego języka, uruchom:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Aby pobrać wszystkie obciążenia i składniki dla wielu języków, uruchom:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Aby pobrać jedno obciążenie dla wszystkich języków, uruchom:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Aby pobrać dwa obciążenia i jeden składnik opcjonalny dla trzech języków, uruchom:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Aby pobrać dwa obciążenia i wszystkie zalecane składniki:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Aby pobrać dwa obciążenia i wszystkie ich zalecane i opcjonalne składniki, uruchom:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Nowość w wersji 15.3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Zapisywanie opcji układu

::: moniker-end

Po uruchomieniu polecenia układu, opcje, które określisz są zapisywane (takie jak obciążenia i języki). Kolejne polecenia układu będą zawierać wszystkie poprzednie opcje.  Oto przykład układu z jednym obciążeniem tylko w języku angielskim:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Aby zaktualizować ten układ do nowszej wersji, nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia są zapisywane i używane przez kolejne polecenia układu w tym folderze układu.  Następujące polecenie zaktualizuje istniejący układ częściowy.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Jeśli chcesz dodać dodatkowe obciążenie, oto przykład, jak to zrobić. W takim przypadku dodamy obciążenie platformy Azure i zlokalizowany język.  Teraz zarówno zarządzane pulpitu i platformy Azure są uwzględnione w tym układzie.  Zasoby językowe dla języka angielskiego i niemieckiego są uwzględniane dla wszystkich tych obciążeń. Układ zostanie zaktualizowany do najnowszej dostępnej wersji.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Jeśli chcesz zaktualizować istniejący układ do pełnego układu, użyj opcji --all, jak pokazano w poniższym przykładzie.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Wdrażanie z instalacji sieciowej

Administratorzy mogą wdrażać program Visual Studio na klienckich stacjach roboczych w ramach skryptu instalacyjnego. Lub użytkownicy, którzy mają uprawnienia administratora można uruchomić instalatora bezpośrednio z udziału, aby zainstalować program Visual Studio na swoim komputerze.

* Użytkownicy mogą zainstalować, uruchamiając następujące polecenie: <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Administratorzy mogą zainstalować w trybie nienadzorowanym, uruchamiając następujące polecenie:

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Aby zapobiec błędowi, upewnij się, że ścieżka pełnego układu jest mniejsza niż 80 znaków.

> [!TIP]
> Po wykonaniu jako część pliku `--wait` wsadowego, `vs_enterprise.exe` opcja zapewnia, że proces czeka, aż instalacja zostanie zakończona, zanim zwróci kod zakończenia.
>
> Jest to przydatne, jeśli administrator przedsiębiorstwa chce wykonać dalsze akcje w zakończeniu instalacji (na przykład, aby [zastosować klucz produktu do pomyślnej instalacji),](automatically-apply-product-keys-when-deploying-visual-studio.md)ale musi czekać na zakończenie instalacji do obsługi kodu zwrotnego z tej instalacji.
>
> Jeśli nie `--wait`używasz, `vs_enterprise.exe` proces kończy się przed zakończeniem instalacji i zwraca niedokładny kod zakończenia, który nie reprezentuje stanu operacji instalacji.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> W przypadku instalacji w trybie offline, jeśli zostanie wyświetlony komunikat o błędzie z napisem `--noweb` "Nie można odnaleźć produktu pasującego do następujących parametrów", upewnij się, że używasz przełącznika w wersji 16.3.5 lub nowszej.
>
::: moniker-end

Po zainstalowaniu z układu, zawartość, która jest instalowana jest pobierana z układu. Jeśli jednak wybierzesz składnik, który nie znajduje się w układzie, zostanie on nabyty z Internetu.  Jeśli chcesz uniemożliwić instalatorowi programu Visual Studio pobieranie zawartości, której `--noWeb` brakuje w układzie, użyj tej opcji. Jeśli `--noWeb` jest używany, a w układzie brakuje zawartości wybranej do zainstalowania, instalacja nie powiedzie się.

> [!TIP]
> Jeśli chcesz zainstalować ze źródła w trybie offline na komputerze `--noWeb` `--noUpdateInstaller` niezłączonym z Internetem, określ zarówno opcje, jak i opcje. Ten pierwszy zapobiega pobieraniu zaktualizowanych obciążeń, składników i tak dalej. Ten ostatni uniemożliwia instalatorowi samoaktualizowanie się z sieci Web.

> [!IMPORTANT]
> Ta `--noWeb` opcja nie uniemożliwia instalacji programu Visual Studio na komputerze podłączonym do Internetu sprawdzania dostępności aktualizacji. Aby uzyskać więcej informacji, zobacz [aktualizacje kontroli do sieciowych wdrożeń programu Visual Studio.](controlling-updates-to-visual-studio-deployments.md)

### <a name="error-codes"></a>Kody błędów

Jeśli użyto `--wait` parametru, w zależności od wyniku `%ERRORLEVEL%` operacji zmienna środowiskowa jest ustawiona na jedną z następujących wartości:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Aktualizowanie układu instalacji sieciowej

W miarę udostępniania aktualizacji produktów można [zaktualizować układ instalacji sieciowej](update-a-network-installation-of-visual-studio.md) w celu uwzględnienia zaktualizowanych pakietów.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Jak utworzyć układ dla poprzedniej wersji programu Visual Studio

::: moniker range="vs-2017"

> [!NOTE]
> Program Visual Studio, które są dostępne w [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) pobrać i zainstalować najnowszą wersję programu Visual Studio, która jest dostępna za każdym razem, gdy są one uruchamiane.
>
> Tak jeśli pobierzesz *program inich wartowniczy* programu Visual Studio dzisiaj i uruchomić go za sześć miesięcy od teraz, instaluje wydanie programu Visual Studio, który jest aktualny w momencie uruchomienia programu iniekcyjny.
>
> Ale jeśli utworzysz *układ,* a następnie zainstalujesz z niego, układ zainstaluje określoną wersję programu Visual Studio, która istnieje w układzie. Mimo że nowsza wersja może istnieć w trybie online, otrzymasz wersję programu Visual Studio, która znajduje się w układzie.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Program Visual Studio, które są dostępne w [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads) pobrać i zainstalować najnowszą wersję programu Visual Studio, która jest dostępna za każdym razem, gdy są one uruchamiane.
>
> Tak jeśli pobierzesz *program inich wartowniczy* programu Visual Studio dzisiaj i uruchomić go za sześć miesięcy od teraz, instaluje wydanie programu Visual Studio, który jest aktualny w momencie uruchomienia programu iniekcyjny.
>
> Ale jeśli utworzysz *układ,* a następnie zainstalujesz z niego, układ zainstaluje określoną wersję programu Visual Studio, która istnieje w układzie. Mimo że nowsza wersja może istnieć w trybie online, otrzymasz wersję programu Visual Studio, która znajduje się w układzie.

::: moniker-end

Jeśli chcesz utworzyć układ dla starszej wersji programu [https://my.visualstudio.com](https://my.visualstudio.com) Visual Studio, przejdź do pobrania "stałych" wersji programów inichowanych programu Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak uzyskać pomoc techniczną dla instalatora w trybie offline

Jeśli wystąpi problem z instalacją w trybie offline, chcemy o tym wiedzieć. Najlepszym sposobem, aby nam to powiedzieć, jest użycie narzędzia [Zgłoś problem.](../ide/how-to-report-a-problem-with-visual-studio.md) Korzystając z tego narzędzia, możesz wysłać nam dane telemetryczne i dzienniki, których potrzebujemy, aby pomóc nam zdiagnozować i rozwiązać problem.

Oferujemy również opcję obsługi [**czatu instalacyjnego**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) w przypadku problemów związanych z instalacją.

Mamy również inne opcje wsparcia. Aby uzyskać listę, zobacz naszą stronę [opinie.](../ide/feedback-options.md)

## <a name="see-also"></a>Zobacz też

- [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
- [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania lub używania programu Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
- [Cykl życia produktu i serwis programu Visual Studio](/visualstudio/releases/2019/servicing/)
- [Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi](update-servicing-baseline.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
- [Instalowanie certyfikatów wymaganych do instalacji programu Visual Studio w trybie offline](/install-certificates-for-visual-studio-offline.md)