---
title: Tworzenie instalacji w trybie offline
description: Dowiedz się, jak zainstalować program Visual Studio w trybie offline, gdy masz zawodne połączenie internetowe lub niską przepustowość.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d52dd064e895b1e35230b93c85a7a8499032943e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114835"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Tworzenie instalacji w trybie offline programu Visual Studio

::: moniker range="vs-2017"

Program Visual Studio 2017 zaprojektował program Visual Studio 2017, aby działał dobrze w różnych konfiguracjach sieci i komputerów. Chociaż zaleca się wypróbowanie [instalatora](https://visualstudio.microsoft.com/vs/older-downloads)&mdash;sieci web programu Visual Studio, który jest małym plikiem&mdash;i pozwala zachować aktualność ze wszystkimi najnowszymi poprawkami i funkcjami, które rozumiemy, że możesz nie być w stanie.

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio 2019 zaprojektował program Visual Studio 2019, aby działał dobrze w różnych konfiguracjach sieci i komputerów. Chociaż zaleca się wypróbowanie [instalatora](https://visualstudio.microsoft.com/downloads)&mdash;sieci web programu Visual Studio, który jest małym plikiem&mdash;i pozwala zachować aktualność ze wszystkimi najnowszymi poprawkami i funkcjami, które rozumiemy, że możesz nie być w stanie.

::: moniker-end

Na przykład może mieć zawodne połączenie internetowe lub takie, które ma niską przepustowość. Jeśli tak, masz kilka opcji: możesz użyć nowej funkcji "Pobierz wszystko, a następnie zainstaluj", aby pobrać pliki przed instalacją, lub użyć wiersza polecenia do utworzenia lokalnej pamięci podręcznej plików.

> [!NOTE]
> Jeśli jesteś administratorem przedsiębiorstwa, który chce przeprowadzić wdrożenie programu Visual Studio w sieci stacji roboczych klienckich, które są zaporowe z Internetu, zobacz nasze [Tworzenie instalacji sieciowej programu Visual Studio](../install/create-a-network-installation-of-visual-studio.md) i [instalowanie certyfikatów wymaganych dla stron instalacji w trybie offline programu Visual Studio.](../install/install-certificates-for-visual-studio-offline.md)

## <a name="use-the-download-all-then-install-feature"></a>Użyj funkcji "Pobierz wszystko, a następnie zainstaluj"

::: moniker range="vs-2017"

[**Nowość w wersji 15.8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): Po pobraniu instalatora internetowego wybierz nową opcję **Pobierz wszystko, a następnie zainstaluj** z Instalatora programu Visual Studio. Następnie kontynuuj instalację.

   ![Opcja "Pobierz wszystko, a następnie zainstaluj"](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

Po pobraniu instalatora sieci Web wybierz nową **opcję Pobierz wszystko, a następnie zainstaluj** z Instalatora programu Visual Studio. Następnie kontynuuj instalację.

   ![Opcja "Pobierz wszystko, a następnie zainstaluj"](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Zaprojektowaliśmy funkcję "Pobierz wszystko, a następnie zainstaluj", dzięki czemu można pobrać program Visual Studio jako pojedynczą instalację dla tego samego komputera, na którym została pobrana. W ten sposób można bezpiecznie odłączyć się od sieci Web przed zainstalowaniem programu Visual Studio.

> [!IMPORTANT]
> Nie używaj funkcji "Pobierz wszystko, a następnie zainstaluj", aby utworzyć pamięć podręczną trybu offline, którą zamierzasz przenieść na inny komputer. Nie jest przeznaczony do pracy w ten sposób. <br><br>Jeśli chcesz utworzyć pamięć podręczną trybu offline w celu zainstalowania programu Visual Studio na innym komputerze, zobacz [wiersz polecenia Użyj wiersza polecenia, aby utworzyć lokalną pamięć podręczną](#use-the-command-line-to-create-a-local-cache) tej strony, aby uzyskać informacje dotyczące tworzenia lokalnej pamięci podręcznej, lub stronę [Tworzenie instalacji sieciowej programu Visual Studio,](../install/create-a-network-installation-of-visual-studio.md) aby uzyskać informacje dotyczące tworzenia pamięci podręcznej sieciowej.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Tworzenie lokalnej pamięci podręcznej za pomocą wiersza polecenia

Po pobraniu małego programu inichowania użyj wiersza polecenia, aby utworzyć lokalną pamięć podręczną. Następnie użyj lokalnej pamięci podręcznej, aby zainstalować program Visual Studio. (Ten proces zastępuje pliki ISO, które były dostępne dla poprzednich wersji).

Oto jak to zrobić.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 - Pobierz program inichuracjowy programu Visual Studio

Aby wykonać ten krok, musisz mieć połączenie z Internetem.

::: moniker range="vs-2017"

Aby uzyskać program uruchamiany dla programu Visual Studio 2017, zobacz stronę pobierania [poprzednich wersji programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/) aby uzyskać szczegółowe informacje na ten temat.

Plik wykonywalny konfiguracji lub bardziej&mdash;&mdash;szczegółowy plik programu inichowania powinien być zgodny lub podobny do jednego z poniższych.

| Wersja | Pod nazwą |
|-------------|-----------------------|
|Visual Studio Community | vs_community.exe |
|Visual Studio Professional | vs_professional.exe |
|Visual Studio Enterprise | vs_enterprise.exe |
|Visual Studio Build Tools   | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Rozpocznij od pobrania programu inichowania programu Visual Studio dla wybranej wersji programu Visual Studio. Plik&mdash;instalacyjny&mdash;lub program inichowania będzie zgodny lub podobny do jednego z poniższych.

| Wersja                    | Plik                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

>[!TIP]
>Jeśli wcześniej pobrano plik boottrappera i chcesz zweryfikować jego wersję, oto jak to zrobić. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inikuscyjny, wybierz polecenie **Właściwości**, wybierz kartę **Szczegóły,** a następnie wyświetl numer **wersji produktu.** Aby dopasować tę liczbę do wersji programu Visual Studio, zobacz [numery kompilacji programu Visual Studio i daty wydania](visual-studio-build-numbers-and-release-dates.md) strony.

### <a name="step-2---create-a-local-install-cache"></a>Krok 2 - Tworzenie lokalnej pamięci podręcznej instalacji

Aby wykonać ten krok, musisz mieć połączenie z Internetem.

> [!IMPORTANT]
> Jeśli zainstalujesz visual studio społeczności, należy aktywować go w ciągu 30 dni od instalacji. Wymaga to połączenia z Internetem.

Otwórz wiersz polecenia i użyj jednego z poleceń z następujących przykładów. Przykłady, które są wymienione w tym miejscu, zakładamy, że używasz wersji społeczności programu Visual Studio; odpowiednio do wersji.

> [!TIP]
> Aby zapobiec błędowi, upewnij się, że pełna ścieżka instalacji jest mniejsza niż 80 znaków.

- W przypadku tworzenia sieci Web i pulpitu .NET w sieci Web i .NET uruchom:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- W przypadku tworzenia komputerów z komputerem i pakietem Office w sieci .NET uruchom:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- W przypadku tworzenia pulpitu w języku C++ uruchom:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Aby utworzyć kompletny układ lokalny ze wszystkimi funkcjami _lots_ (zajmie to dużo czasu!)&mdash;uruchom:

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Kompletny układ programu Visual Studio wymaga co najmniej 35 GB miejsca na dysku. Aby uzyskać więcej informacji, zobacz [Wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs/). Aby uzyskać informacje dotyczące tworzenia układu tylko ze składnikami, które chcesz zainstalować, zobacz [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia.](use-command-line-parameters-to-install-visual-studio.md)

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Kompletny układ programu Visual Studio wymaga co najmniej 35 GB miejsca na dysku. Aby uzyskać więcej informacji, zobacz [Wymagania systemowe](/visualstudio/releases/2019/system-requirements/). Aby uzyskać informacje dotyczące tworzenia układu tylko ze składnikami, które chcesz zainstalować, zobacz [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia.](use-command-line-parameters-to-install-visual-studio.md)

::: moniker-end

Jeśli chcesz zainstalować język inny niż `en-US` angielski, zmień ustawienia regionalne z [listy ustawień regionalnych języka](#list-of-language-locales). Następnie użyj [listy składników i obciążeń dostępnych](workload-and-component-ids.md) do dalszego dostosowywania pamięci podręcznej instalacji.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3 — instalowanie programu Visual Studio z lokalnej pamięci podręcznej

> [!TIP]
> Po uruchomieniu z lokalnej pamięci podręcznej instalacji instalator używa lokalnych wersji każdego z tych plików. Jeśli jednak podczas instalacji wybrano składniki, których nie ma w pamięci podręcznej, instalator spróbuje pobrać je z Internetu.

::: moniker range="vs-2019"
> [!IMPORTANT]
> W przypadku instalacji w trybie offline, jeśli zostanie wyświetlony komunikat o błędzie z napisem `--noweb` "Nie można odnaleźć produktu pasującego do następujących parametrów", upewnij się, że używasz przełącznika w wersji 16.3.5 lub nowszej.
>
::: moniker-end

Aby upewnić się, że instalujesz tylko pliki, które zostały wcześniej pobrane, użyj tych samych opcji wiersza polecenia, które zostały użyte do utworzenia pamięci podręcznej układu. Na przykład, jeśli utworzono pamięć podręczną układu z następującym poleceniem:

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Następnie użyj tego polecenia, aby uruchomić instalację:

```cmd
c:\vslayout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

Aby uzyskać więcej przykładów używania [parametrów wiersza polecenia,](use-command-line-parameters-to-install-visual-studio.md)zobacz [przykłady parametrów wiersza polecenia dla strony instalacji programu Visual Studio.](command-line-parameter-examples.md) 

> [!NOTE]
> Jeśli zostanie wyświetlony błąd, że podpis jest nieprawidłowy, należy zainstalować zaktualizowane certyfikaty. Otwórz folder Certyfikaty w pamięci podręcznej trybu offline. Kliknij dwukrotnie każdy z plików certyfikatów, a następnie kliknij kreatora Menedżera certyfikatów. Jeśli zostaniesz poproszony o podanie hasła, pozostaw to puste.

### <a name="list-of-language-locales"></a>Lista ustawień regionalnych języka

| **Ustawienia regionalne języka** | **Język** |
| ----------------------- | --------------- |
| cs-CZ | Czeski |
| de-DE | Niemiecki |
| pl-PL | Polski |
| es-ES | Hiszpański |
| fr-FR | Francuski |
| it-IT | Włoski |
| ja-JP | Japoński |
| ko-KR | Koreański |
| pl-PL | Polski |
| pt-BR | Portugalski (Brazylia) |
| ru-RU | Rosyjski |
| tr-TR | Turecki |
| zh-CN | Chiński - Uproszczony |
| zh-TW | Chiński - Tradycyjny |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Tworzenie instalacji sieciowej programu Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Instalowanie certyfikatów wymaganych do instalacji programu Visual Studio w trybie offline](../install/install-certificates-for-visual-studio-offline.md)
- [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
