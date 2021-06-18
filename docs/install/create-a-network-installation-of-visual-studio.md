---
title: Tworzenie instalacji opartej na sieci
description: Dowiedz się, jak utworzyć punkt instalacji sieci na Visual Studio w przedsiębiorstwie.
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
ms.openlocfilehash: 080c4450cfcdca28386811865229af75303beb6a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307534"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Tworzenie instalacji sieciowej Visual Studio

Czasami administrator przedsiębiorstwa chce utworzyć punkt instalacji sieci, który zawiera Visual Studio plików, które można wdrożyć na klienckich stacjach roboczych. Ma to na celu ułatwienie scenariuszy, w których maszyny klienckie mogą mieć ograniczone uprawnienia lub ograniczony dostęp do Internetu lub gdy zespoły wewnętrzne chcą wykonać testowanie zgodności, zanim ich organizacja standaryzuje określoną wersję zestawu narzędzi dla deweloperów. Zaprojektowaliśmy usługę Visual Studio tak, aby  administrator mógł utworzyć układ sieci, który zasadniczo tworzy pamięć podręczną plików znajdującą się w wewnętrznym statycznym udziałze sieciowym, który zawiera wszystkie pliki Visual Studio zarówno dla instalacji początkowej, jak i wszystkich przyszłych aktualizacji produktów.

 > [!NOTE]
 >  - Jeśli masz wiele wersji programu Visual Studio w użyciu w przedsiębiorstwie (na przykład zarówno wersji Visual Studio Professional, jak i Visual Studio 2019 Enterprise), musisz utworzyć osobny udział instalacji sieciowej dla każdej wersji.
 >  - Zaleca się podjęcie decyzji o tym, w jaki sposób klienci mają otrzymywać aktualizacje produktów _przed_ początkową zainstalowaniem klienta.  Ułatwia to zapewnienie prawidłowego ustawienia opcji konfiguracji. Do wyboru są m.in. informacje o tym, że klienci mogą pobrać aktualizacje z lokalizacji układu sieciowego lub z Internetu. 
 >  - Oryginalny układ Visual Studio instalacji i wszystkie kolejne aktualizacje produktu muszą znajdować się w tym samym katalogu sieciowym, aby zapewnić prawidłowe działanie funkcji naprawy i odinstalowywania.

## <a name="download-the-visual-studio-bootstrapper"></a>Pobieranie Visual Studio inicjujący

Pobierz plik programu inicjujący dla wersji Visual Studio, której chcesz użyć. Upewnij się, że wybierz **pozycję Zapisz,** a następnie wybierz **pozycję Otwórz folder.**

::: moniker range="vs-2017"

Aby uzyskać najnowszy program inicjujący dla programu Visual Studio 2017 w wersji 15.9, przejdź do strony [programu Visual Studio poprzednie wersje](https://visualstudio.microsoft.com/vs/older-downloads/) i pobierz jeden z następujących plików programu inicjjącego:

| Wersja                                      | Pod nazwą            |
|----------------------------------------------|---------------------|
| Visual Studio 2017 Enterprise w wersji 15.9   | vs_enterprise.exe   |
| Visual Studio 2017 Professional w wersji 15.9 | vs_professional.exe |
| Visual Studio 2017 Build Tools w wersji 15.9  | vs_buildtools.exe   |

Inne obsługiwane programy inicjujące to vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe i vs_testprofessional.exe.

::: moniker-end

::: moniker range="vs-2019"

Zacznij od pobrania programu inicjjącego programu Visual Studio 2019 ze strony pobierania aplikacji [Visual Studio](https://visualstudio.microsoft.com/downloads) lub strony wydań programu [Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) dla wybranej wersji i wydania Visual Studio.  Plik wykonywalny instalatora lub plik programu inicjujący będzie odpowiadać lub być podobny do &mdash; &mdash; jednego z następujących:

| Wersja                    | Pobierz                                                                                                                                                                                                                           |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019)     |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

Inne obsługiwane programy inicjujące to [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)i [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

::: moniker range=">=vs-2022"

>![!TIP]
> Wydane wersje programu Visual Studio 2022 nie są jeszcze dostępne. Program inicjujący poniżej jest dostępny w wersji zapoznawczej Visual Studio 2022 r.
Rozpocznij od pobrania programu inicjjącego Visual Studio 2022 z Visual Studio [pobierania.](https://aka.ms/vs2022preview)

| Wersja                    | Pobierz                                                                             |
|----------------------------|--------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_enterprise.exe)     |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_professional.exe) |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjujący i chcesz sprawdzić, jaka jest jego wersja, oto jak to zrobić. W systemie Windows otwórz Eksplorator plików kliknij prawym przyciskiem myszy plik programu  inicjjącego, wybierz pozycję **Właściwości,** wybierz kartę Szczegóły, a następnie wyświetl **numer wersji** produktu. Aby dopasować ten numer do wersji Visual Studio, zobacz Visual Studio [kompilacji i daty wydania](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjujący i chcesz sprawdzić, jaka jest jego wersja, oto jak to zrobić. W systemie Windows otwórz Eksplorator plików kliknij prawym przyciskiem myszy plik programu  inicjjącego, wybierz pozycję **Właściwości,** wybierz kartę Szczegóły, a następnie wyświetl **numer wersji** produktu. Aby dopasować ten numer do wersji Visual Studio, zobacz [Visual Studio 2019](/visualstudio/releases/2019/history).

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjujący i chcesz sprawdzić, jaka jest jego wersja, oto jak to zrobić. W systemie Windows otwórz Eksplorator plików kliknij prawym przyciskiem myszy plik programu  inicjjącego, wybierz pozycję **Właściwości,** wybierz kartę Szczegóły, a następnie wyświetl **numer wersji** produktu. Aby dopasować ten numer do wersji Visual Studio, zobacz [Visual Studio 2022.](/visualstudio/releases/2022/history)

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Tworzenie folderu instalacji w trybie offline

Aby wykonać ten krok, musisz mieć połączenie internetowe.

Otwórz wiersz polecenia, przejdź do katalogu, do którym został pobrany program inicjujący, i użyj parametrów programu inicjujący zgodnie z definicją na stronie Instalowanie programu [Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) przy użyciu parametrów wiersza polecenia w celu utworzenia i obsługi pamięci podręcznej instalacji sieci. Typowe przykłady tworzenia układów początkowych przedstawiono poniżej i w przykładach parametrów wiersza polecenia dla [Visual Studio instalacji](../install/command-line-parameter-examples.md).  

   > [!IMPORTANT]
   > Pełny początkowy układ dla jednego języka wymaga około 35 GB miejsca na dysku dla Visual Studio Community i 42 GB na Visual Studio Enterprise. Dodatkowe [ustawienia lokalne języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) wymagają około pół GB każdy. Zobacz [sekcję Dostosowywanie układu sieci,](#customize-the-network-layout) aby uzyskać więcej informacji. Należy pamiętać, że kolejne aktualizacje układu muszą być również przechowywane w tej samej lokalizacji sieciowej, więc należy oczekiwać, że zawartość katalogu lokalizacji układu sieciowego może z czasem być dość duża.  

- Aby utworzyć początkowy układ Visual Studio Enterprise ze wszystkimi językami i wszystkimi funkcjami, uruchom:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Aby utworzyć początkowy układ Visual Studio Professional ze wszystkimi językami i wszystkimi funkcjami, uruchom:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Modyfikowanie response.jspliku

Można zmodyfikować `response.json` plik, aby ustawić wartości domyślne, które są używane podczas uruchamiania instalatora.  Można na przykład skonfigurować plik tak, aby wybierał określony zestaw obciążeń, które `response.json` mają być wybierane automatycznie. Można również skonfigurować , aby określić, czy klient powinien odbierać tylko zaktualizowane `response.json` pliki z lokalizacji układu sieciowego. Aby uzyskać więcej informacji, zobacz [Automatyzowanie Visual Studio instalacji za pomocą pliku odpowiedzi](../install/automated-installation-with-response-file.md). 

Jeśli wystąpi problem z programem inicjujący programu Visual Studio, który zgłasza błąd podczas parowania go z plikiem, zobacz Rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania lub używania Visual Studio, aby uzyskać `response.json` więcej informacji. [](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process)

## <a name="copy-the-layout-to-a-network-share"></a>Kopiowanie układu do udziału sieciowego

Hostuj układ w udziałach sieciowych, aby można go było uruchamiać z maszyn klienckich.

W poniższym przykładzie [`xcopy`](/windows-server/administration/windows-commands/xcopy/) użyto . Możesz również użyć [`robocopy`](/windows-server/administration/windows-commands/robocopy/) , jeśli chcesz.

::: moniker range="vs-2017"

Przykład:

```shell
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```shell
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

::: moniker range=">=vs-2022"

```shell
xcopy /e c:\VSLayout \\server\products\VS2022
```

::: moniker-end

> [!IMPORTANT]
> Aby zapobiec błędowi, upewnij się, że pełna ścieżka układu jest mniejsza niż 80 znaków.

## <a name="customize-the-network-layout"></a>Dostosowywanie układu sieci

Istnieje kilka opcji, których można użyć do dostosowania układu sieci. Możesz utworzyć układ częściowy, który zawiera [](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)tylko określony zestaw języków, obciążeń, składników i ich zalecanych lub [opcjonalnych zależności.](workload-and-component-ids.md) Może to być przydatne, jeśli wiesz, że zamierzasz wdrożyć tylko podzbiór obciążeń na klienckich stacjach roboczych. Typowe parametry wiersza polecenia do dostosowywania układu to:

* `--add`w celu [określenia identyfikatorów obciążeń lub składników.](workload-and-component-ids.md) <br>Jeśli `--add` jest używany, pobierane są tylko te obciążenia i składniki określone `--add` za pomocą .  Jeśli `--add` nie jest używany, pobierane są wszystkie obciążenia i składniki.
* `--includeRecommended` aby uwzględnić wszystkie zalecane składniki dla określonych identyfikatorów obciążeń
* `--includeOptional` aby uwzględnić wszystkie zalecane i opcjonalne składniki dla określonych identyfikatorów obciążeń.
* `--lang` , aby [określić ustawienia lokalne języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Poniżej przedstawiono kilka przykładów tworzenia niestandardowego układu częściowego.

* Aby pobrać wszystkie obciążenia i składniki tylko dla jednego języka, uruchom:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Aby pobrać wszystkie obciążenia i składniki dla wielu języków, uruchom:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Aby pobrać jedno obciążenie dla wszystkich języków, uruchom:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Aby pobrać dwa obciążenia i jeden składnik opcjonalny dla trzech języków, uruchom:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Aby pobrać dwa obciążenia i wszystkie zalecane składniki:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Aby pobrać dwa obciążenia oraz wszystkie ich zalecane i opcjonalne składniki, uruchom:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

### <a name="save-your-layout-options"></a>Zapisywanie opcji układu

Po uruchomieniu polecenia układu określone opcje są zapisywane (na przykład obciążenia i języki). Kolejne polecenia układu będą zawierać wszystkie poprzednie opcje.  Oto przykład układu z jednym obciążeniem tylko dla języka angielskiego:

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Jeśli chcesz zaktualizować ten układ do nowszej wersji, nie musisz określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia są zapisywane i używane przez wszystkie kolejne polecenia układu w tym folderze układu.  Następujące polecenie spowoduje zaktualizowanie istniejącego układu częściowego.

```shell
vs_enterprise.exe --layout c:\VSLayout
```

Jeśli chcesz dodać dodatkowe obciążenie, oto przykład, jak to zrobić. W tym przypadku dodamy obciążenie platformy Azure i zlokalizowany język.  Teraz ten układ obejmuje zarówno program Managed Desktop, jak i platformę Azure.  Zasoby językowe dla języka angielskiego i niemieckiej są uwzględniane dla wszystkich tych obciążeń. Układ został zaktualizowany do najnowszej dostępnej wersji.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Jeśli chcesz zaktualizować istniejący układ do pełnego układu, użyj opcji --all, jak pokazano w poniższym przykładzie.

```shell
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Wdrażanie z instalacji sieciowej

Administratorzy mogą Visual Studio na klienckich stacjach roboczych w ramach skryptu instalacji. Użytkownicy z uprawnieniami administratora mogą też uruchamiać instalatora bezpośrednio z udziału, aby Visual Studio na swojej maszynie.

* Użytkownicy mogą zainstalować program , uruchamiając następujące polecenie: <br>

    ```shell
    \\server\products\VS\vs_enterprise.exe
    ```

* Administratorzy mogą instalować w trybie nienadzorowany, uruchamiając następujące polecenie:

    ```shell
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Aby zapobiec błędowi, upewnij się, że pełna ścieżka układu jest mniejsza niż 80 znaków.

> [!TIP]
> W przypadku wykonywania w ramach pliku wsadowego opcja zapewnia, że proces czeka, aż instalacja zostanie ukończona, zanim zwróci `--wait` `vs_enterprise.exe` kod zakończenia.
>
> Jest to przydatne, jeśli administrator przedsiębiorstwa chce wykonać dodatkowe akcje w ramach ukończonej instalacji (na przykład w celu zastosowania klucza produktu do pomyślnej [instalacji),](automatically-apply-product-keys-when-deploying-visual-studio.md)ale musi poczekać na zakończenie instalacji, aby obsłużyć kod powrotny z tej instalacji.
>
> Jeśli nie używasz programu , proces kończy działanie przed ukończeniem instalacji i zwraca niedokładny kod zakończenia, który nie reprezentuje stanu `--wait` `vs_enterprise.exe` operacji instalacji.
>

::: moniker range=">=vs-2019"
> [!IMPORTANT]
> Jeśli w przypadku instalacji w trybie offline zostanie wyświetlony komunikat o błędzie "Nie można odnaleźć produktu zgodnego z następującymi parametrami", upewnij się, że używasz przełącznika w wersji `--noweb` 16.3.5 lub nowszej.
>
::: moniker-end

Podczas instalacji z układu instalowana zawartość jest instalowana z układu. Jeśli jednak wybierzesz składnik, który nie znajduje się w układzie, zostanie on uzyskany z Internetu.  Jeśli chcesz uniemożliwić instalatorowi Visual Studio pobieranie zawartości, której brakuje w układzie, użyj `--noWeb` opcji . Jeśli jest używany, a w układzie brakuje zawartości wybranej do `--noWeb` zainstalowania, instalacja nie powiedzie się.

> [!TIP]
> Jeśli chcesz zainstalować ze źródła w trybie offline na komputerze bez połączenia z Internetem, określ opcje `--noWeb` i `--noUpdateInstaller` . Pierwszy uniemożliwia pobieranie zaktualizowanych obciążeń, składników i tak dalej. Ta ostatnia uniemożliwia instalatorowi samodzielne aktualizowanie z Internetu.

> [!IMPORTANT]
> Ta opcja nie Visual Studio sprawdzania aktualizacji na komputerze połączonym z `--noWeb` Internetem. Aby uzyskać więcej informacji, zobacz [stronę Kontrolowanie aktualizacji wdrożeń Visual Studio sieciowych.](controlling-updates-to-visual-studio-deployments.md)

### <a name="error-codes"></a>Kody błędów

Jeśli używasz parametru , w zależności od wyniku operacji zmienna środowiskowa jest ustawiana na jedną `--wait` `%ERRORLEVEL%` z następujących wartości:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Aktualizowanie układu instalacji sieci

W związku z tym, że aktualizacje produktów stają się dostępne, warto [zaktualizować](update-a-network-installation-of-visual-studio.md) układ instalacji sieci w celu uwzględnienia zaktualizowanych pakietów.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Jak utworzyć układ dla poprzedniej Visual Studio wersji

Najpierw musisz zrozumieć, że istnieją dwa typy programu inicjjącego Visual Studio — jeden, który można scharakteryzować słowami "latest", "current", "evergreen" i "tip" oraz jeden, który zasadniczo oznacza "stałą wersję". Oba typy plików programu inicjjącego mają dokładnie taką samą nazwę, a najlepszym sposobem odróżnienia tego typu jest zwrócenie uwagi na to, skąd pochodzi. Program inicjujący Visual Studio dostępny na stronie pobierania plików do programu [Visual Studio](https://visualstudio.microsoft.com/downloads) jest uznawany za zawszezielony program inicjujący Visual Studio i zawsze instalują (lub aktualizują) najnowsze wydanie dostępne w kanale podczas uruchamiania programu inicjjącego. Program inicjujący Visual Studio dostępny na stronie wydań programu [Visual Studio 2019](/visualstudio/releases/2019/history) Visual Studio [2022](/visualstudio/releases/2022/history)  lub które są osadzone wewnątrz aktualizacji administratora w katalogu usługi Microsoft Update, instalują określoną stałą wersję produktu.

Dlatego jeśli pobierzesz program inicjujący Visual Studio evergreen dzisiaj i uruchomisz go sześć miesięcy od teraz, zainstaluje wersję programu Visual Studio, która jest aktualna w czasie uruchamiania programu inicjjącego. Jest ona zaprojektowana tak, aby zawsze instalować najnowsze bity i zapewniać aktualną wersję.

Jeśli pobierzesz program inicjujący o stałym linku lub jeśli uruchomisz aktualizację administratora pobraną z katalogu firmy Microsoft, program zawsze zainstaluje określoną wersję produktu, niezależnie od tego, kiedy został uruchomiony.

Na koniec możesz utworzyć układ sieci przy użyciu dowolnego z tych programów inicjujący, a wersja, która zostanie utworzona w układzie, zależy od programu inicjjącego, który jest przez Ciebie, na przykład będzie to stała wersja lub bieżąca wersja. Następnie możesz zaktualizować układ sieci przy użyciu dowolnego późniejszego programu inicjatora lub użyć pakietu aktualizacji administratora z katalogu Microsoft Update inicjatora. Niezależnie od tego, jak aktualizujesz układ, wynikowy zaktualizowany układ będzie pamięcią podręczną pakietu zawierającą określoną wersję produktu, a następnie będzie zachowywać się jak stały program inicjujący link. Dlatego za każdym razem, gdy klient zostanie zainstalowany z układu, zainstaluje określoną wersję pakietu Visual Studio, która istnieje w układzie (nawet jeśli nowsza wersja może istnieć w trybie online).

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak uzyskać pomoc techniczną dla instalatora offline

Jeśli wystąpi problem z instalacją w trybie offline, chcemy się o tym dowiedzieć. Najlepszym sposobem, aby nam powiedzieć, jest użycie narzędzia Zgłoś [problem.](../ide/how-to-report-a-problem-with-visual-studio.md) Korzystając z tego narzędzia, możesz wysłać nam dane telemetryczne i dzienniki, których potrzebujemy, aby pomóc nam zdiagnozować i rozwiązać problem.

Oferujemy również opcję obsługi czatu [**instalacyjnego**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) w przypadku problemów związanych z instalacją.

Dostępne są również inne opcje pomocy technicznej. Aby uzyskać listę, zobacz naszą [stronę Opinii.](../ide/feedback-options.md)

## <a name="see-also"></a>Zobacz też

- [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
- [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania lub używania Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Kontrolowanie aktualizacji wdrożeń Visual Studio sieciowych](controlling-updates-to-visual-studio-deployments.md)
- [Visual Studio produktu i jego obsługa](/visualstudio/releases/2019/servicing/)
- [Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi](update-servicing-baseline.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
- [Instalowanie certyfikatów wymaganych do instalacji Visual Studio offline](install-certificates-for-visual-studio-offline.md)
