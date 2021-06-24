---
title: Tworzenie instalacji w trybie offline
description: Dowiedz się, jak Visual Studio w trybie offline, gdy masz zawodne połączenie internetowe lub niską przepustowość.
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b10fc1adbb0b4a6e053549749ea90acf3919d0c6
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602200"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Tworzenie instalacji w trybie offline programu Visual Studio

::: moniker range="vs-2017"

Zaprojektowaliśmy program Visual Studio 2017, aby działał dobrze w różnych konfiguracjach sieci i komputerów. Mimo że zalecamy wypróbowanie instalatora internetowego usługi [Visual Studio, który](https://visualstudio.microsoft.com/vs/older-downloads)jest małym plikiem, który pozwala być na najnowsze poprawki i funkcje, zdajemy sobie sprawę, że być może nie jest to &mdash; &mdash; możliwe.

::: moniker-end

::: moniker range=">=vs-2019"

Zaprojektowaliśmy program Visual Studio 2019 i nowsze, aby działały dobrze w różnych konfiguracjach sieci i komputerów. Mimo że zalecamy wypróbowanie instalatora internetowego usługi [Visual Studio, który](https://visualstudio.microsoft.com/downloads)jest małym plikiem, który pozwala być na najnowsze poprawki i funkcje, zdajemy sobie sprawę, że być może nie jest to &mdash; &mdash; możliwe.

::: moniker-end

Może to być na przykład zawodne połączenie internetowe lub połączenie o niskiej przepustowości. Jeśli tak, masz kilka opcji: możesz użyć nowej funkcji "Pobierz wszystko, a następnie zainstaluj", aby pobrać pliki przed zainstalowaniem, lub użyć wiersza polecenia, aby utworzyć lokalną pamięć podręczną plików.

> [!NOTE]
> Jeśli jesteś administratorem przedsiębiorstwa, który chce przeprowadzić wdrożenie usługi Visual Studio w sieci klienckich stacji roboczych, które są zapór z Internetu, zobacz tworzenie instalacji sieciowej programu [Visual Studio](../install/create-a-network-installation-of-visual-studio.md) i Instalowanie certyfikatów wymaganych na stronach instalacji w trybie offline programu [Visual Studio.](../install/install-certificates-for-visual-studio-offline.md)

## <a name="use-the-download-all-then-install-feature"></a>Użyj funkcji "Pobierz wszystko, a następnie zainstaluj"

::: moniker range="vs-2017"

[**Nowość w wersji 15.8:**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install)po pobraniu instalatora internetowego wybierz nową opcję Pobierz **wszystko,** a następnie zainstaluj ją z Instalator programu Visual Studio. Następnie kontynuuj instalację.

   ![Opcja "Pobierz wszystko, a następnie zainstaluj"](media/download-all-then-install.png)

::: moniker-end

::: moniker range=">=vs-2019"

Po pobraniu instalatora internetowego wybierz nową opcję Pobierz **wszystko,** a następnie zainstaluj ją z Instalator programu Visual Studio. Następnie kontynuuj instalację.

   ![Opcja "Pobierz wszystko, a następnie zainstaluj"](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Zaprojektowaliśmy funkcję "Pobierz wszystko, a następnie zainstaluj", aby można było pobrać aplikację Visual Studio jako pojedynczą instalację dla tego samego komputera, na którym został pobrany. Dzięki temu można bezpiecznie rozłączyć się z Siecią Web przed zainstalowaniem Visual Studio.

> [!IMPORTANT]
> Nie należy używać funkcji "Pobierz wszystko, a następnie zainstaluj" do utworzenia pamięci podręcznej w trybie offline, która ma być przesyłana na inny komputer. Nie jest on przeznaczony do tej pracy. <br><br>Jeśli chcesz utworzyć pamięć podręczną w trybie offline na komputerze lokalnym, której następnie możesz użyć do zainstalowania usługi Visual Studio, zobacz sekcję Tworzenie lokalnej pamięci podręcznej przy użyciu wiersza polecenia [poniżej.](#use-the-command-line-to-create-a-local-cache)  Alternatywnie strona [Tworzenie instalacji sieciowej](../install/create-a-network-installation-of-visual-studio.md) Visual Studio zawiera informacje dotyczące sposobu tworzenia pamięci podręcznej w sieci.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Tworzenie lokalnej pamięci podręcznej przy użyciu wiersza polecenia
::: moniker range="vs-2017"

Po pobraniu małego programu inicjjącego użyj wiersza polecenia, aby utworzyć lokalną pamięć podręczną. Następnie użyj lokalnej pamięci podręcznej, aby zainstalować Visual Studio. (Ten proces zastępuje pliki ISO, które były dostępne dla poprzednich wersji). 

::: moniker-end

::: moniker range=">=vs-2019"

Po pobraniu małego pliku programu inicjjącego użyj wiersza polecenia, aby utworzyć lokalną pamięć podręczną. Następnie użyj lokalnej pamięci podręcznej, aby zainstalować Visual Studio.

::: moniker-end

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1. Pobieranie Visual Studio inicjujący

Aby wykonać ten krok, musisz mieć połączenie internetowe.

::: moniker range="vs-2017"

Aby uzyskać najnowszy program inicjujący dla programu Visual Studio 2017 w wersji 15.9, przejdź do strony [programu Visual Studio poprzednie](https://visualstudio.microsoft.com/vs/older-downloads/) wersje i pobierz jeden z następujących plików programu inicjjącego:

| Wersja                                      | Pod nazwą            |
|----------------------------------------------|---------------------|
| Visual Studio Professional 2017 w wersji 15.9 | vs_professional.exe |
| Visual Studio Enterprise 2017 w wersji 15.9   | vs_enterprise.exe   |
| Visual Studio Build Tools 2017 w wersji 15.9  | vs_buildtools.exe   |

::: moniker-end

::: moniker range="vs-2019"

Zacznij od pobrania programu inicjjącego programu Visual Studio 2019 ze strony pobierania programu [Visual Studio](https://visualstudio.microsoft.com/downloads) lub strony wydań programu [Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) dla wybranej wersji i Visual Studio. Plik instalacyjny lub program inicjujący będą zgodne lub &mdash; będą podobne do jednego z &mdash; następujących:

| Wersja                         | Plik                                                                                                                                                                                                                               |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio 2019 Build Tools  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
> Wydane wersje programu Visual Studio 2022 nie są jeszcze dostępne. Poniższe programy inicjujące są dostępne w wersji zapoznawczej programu Visual Studio 2022.
>Zacznij od pobrania programu inicjjącego Visual Studio 2022 ze [strony pobierania Visual Studio 2022.](https://aka.ms/vs2022preview)

| Wersja                         | Pobierz                                                            |
|---------------------------------|---------------------------------------------------------------------|
| Visual Studio 2022 Professional | [vs_professional.exe](https://aka.ms/vs/17/pre/vs_professional.exe) |
| Visual Studio 2022 Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/pre/vs_enterprise.exe)     |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjujący i chcesz sprawdzić, jaka jest jego wersja, oto jak to zrobić. W systemie Windows otwórz Eksplorator plików, kliknij prawym przyciskiem myszy plik programu  inicjjącego, wybierz pozycję **Właściwości,** wybierz kartę Szczegóły, a następnie wyświetl **numer wersji** produktu. Aby dopasować tę liczbę do wydania Visual Studio, zapoznaj się ze stroną Visual Studio [kompilacji i dat wydania.](/visual-studio-build-numbers-and-release-dates.md)

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjujący i chcesz sprawdzić jego wersję, oto jak to zrobić. W systemie Windows otwórz Eksplorator plików, kliknij prawym przyciskiem myszy plik programu  inicjjącego, wybierz pozycję **Właściwości,** wybierz kartę Szczegóły, a następnie wyświetl **numer wersji** produktu. Aby dopasować tę liczbę do wydania Visual Studio, zapoznaj się ze stroną Visual Studio [2019.](/visualstudio/releases/2019/history)

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjujący i chcesz sprawdzić jego wersję, oto jak to zrobić. W systemie Windows otwórz Eksplorator plików, kliknij prawym przyciskiem myszy plik programu  inicjjącego, wybierz pozycję **Właściwości,** wybierz kartę Szczegóły, a następnie wyświetl **numer wersji** produktu. Aby dopasować tę liczbę do wersji Visual Studio, zapoznaj się ze stroną Visual Studio [2022.](/visualstudio/releases/2022/history)

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>Krok 2. Tworzenie lokalnej pamięci podręcznej instalacji

Aby wykonać ten krok, musisz mieć połączenie internetowe.

Otwórz wiersz polecenia i użyj parametrów programu inicjjącego zgodnie z definicją na stronie Użyj parametrów wiersza polecenia do zainstalowania [Visual Studio,](use-command-line-parameters-to-install-visual-studio.md) aby utworzyć lokalną pamięć podręczną instalacji. Typowe przykłady użycia programu inicjjącego przedsiębiorstwa przedstawiono poniżej i na [stronie przykładów](command-line-parameter-examples.md) parametrów wiersza polecenia. Język inny niż angielski można zainstalować, zmieniając ustawienia lokalne z listy ustawień regionalnych języka na , a do dalszego dostosowywania pamięci podręcznej można użyć listy składników i `en-US` obciążeń. [](#list-of-language-locales) [](workload-and-component-ids.md)

> [!TIP]
> Aby zapobiec błędowi, upewnij się, że pełna ścieżka instalacji jest mniejsza niż 80 znaków.

- W przypadku tworzenia aplikacji klasycznych i internetowych na platformie .NET uruchom:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- W przypadku tworzenia aplikacji klasycznych na platformie .NET i pakietu Office uruchom:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- W przypadku programowania aplikacji klasycznych w języku C++ uruchom:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Aby utworzyć kompletny układ lokalny, tylko w języku angielskim, ze wszystkimi funkcjami (zajmie to dużo czasu, mamy wiele &mdash; funkcji!),  uruchom:

   ```shell
    vs_enterprise.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Pełny układ Visual Studio wymaga co najmniej 35 GB miejsca na dysku. Aby uzyskać więcej informacji, zobacz [Wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs/). 

::: moniker-end

::: moniker range=">=vs-2019"

   > [!NOTE]
   > Pełny układ Visual Studio wymaga co najmniej 41 GB miejsca na dysku. Aby uzyskać więcej informacji, zobacz [Wymagania systemowe](/visualstudio/releases/2019/system-requirements/).

::: moniker-end


### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3. Instalowanie Visual Studio z lokalnej pamięci podręcznej
Podczas instalowania Visual Studio z lokalnej pamięci podręcznej instalacji instalator Visual Studio używa lokalnych wersji plików w pamięci podręcznej. Jeśli jednak podczas instalacji wybierzesz składniki, które nie są w pamięci podręcznej, instalator Visual Studio spróbuje pobrać je z Internetu. Aby upewnić się, że instalujesz tylko pliki, które [](use-command-line-parameters-to-install-visual-studio.md) zostały wcześniej pobrane, użyj tych samych opcji wiersza polecenia, które zostały użyte do utworzenia pamięci podręcznej układu. 

Jeśli na przykład utworzono lokalną pamięć podręczną instalacji przy użyciu następującego polecenia:

```shell
vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Następnie użyj tego polecenia, aby uruchomić instalację:

```shell
c:\vslayout\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!IMPORTANT]
> Jeśli używasz usługi Visual Studio Community, musisz ją aktywować, logując się do produktu w ciągu 30 dni od instalacji. Aktywacja wymaga połączenia internetowego.

> [!NOTE]
> Jeśli wystąpi błąd z nieprawidłowym podpisem, musisz [zainstalować zaktualizowane certyfikaty](install-certificates-for-visual-studio-offline.md). Otwórz folder Certyfikaty w pamięci podręcznej trybu offline. Kliknij dwukrotnie każdy plik certyfikatu, a następnie kliknij za pomocą Kreatora Menedżera certyfikatów. Jeśli zostaniesz poproszony o hasło, pozostaw to pole puste.

::: moniker range=">=vs-2019"
> [!TIP]
> Jeśli w przypadku instalacji w trybie offline zostanie wyświetlony komunikat o błędzie "Nie można odnaleźć produktu pasującego do następujących parametrów", upewnij się, że używasz przełącznika w wersji `--noweb` 16.3.5 lub nowszej.

::: moniker-end

### <a name="list-of-language-locales"></a>Lista lokalizacji regionalnych języka

| **Ustawienia językowe** | **Język**          |
|---------------------|-----------------------|
| cs-CZ               | Czeski                 |
| de-DE               | Niemiecki                |
| en-US               | Angielski               |
| es-ES               | Hiszpański               |
| fr-FR               | Francuski                |
| it-IT               | Włoski               |
| ja-JP               | japoński              |
| ko-KR               | Koreański                |
| pl-PL               | Polski                |
| pt-BR               | Portugalski (Brazylia)   |
| ru-RU               | Rosyjski               |
| tr-TR               | Turecki               |
| zh-CN               | Chiński – uproszczony  |
| zh-TW               | Chiński – tradycyjny |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Tworzenie instalacji sieciowej Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Instalowanie certyfikatów wymaganych do instalacji Visual Studio offline](../install/install-certificates-for-visual-studio-offline.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
