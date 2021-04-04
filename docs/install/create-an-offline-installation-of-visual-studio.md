---
title: Tworzenie instalacji w trybie offline
description: Dowiedz się, jak zainstalować program Visual Studio w trybie offline, gdy masz zawodne połączenie internetowe lub niska przepustowość.
ms.date: 3/29/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8c4815540a5911ca0193a89a237a3c4d690c4dba
ms.sourcegitcommit: 22789927ec8e877b7d2b67a555d6df97d84103e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2021
ms.locfileid: "105981306"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Tworzenie instalacji w trybie offline programu Visual Studio

::: moniker range="vs-2017"

Program Visual Studio 2017 został zaprojektowany tak, aby działał prawidłowo w różnych konfiguracjach sieci i komputerów. Mimo że zalecamy wypróbowanie [Instalatora sieci Web programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads), &mdash; który jest małym plikiem, który pozwala na bieżąco korzystać ze wszystkich najnowszych poprawek i funkcji, &mdash; które rozumiemy, że może to nie być możliwe.

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio 2019 został zaprojektowany tak, aby działał prawidłowo w różnych konfiguracjach sieci i komputerów. Mimo że zalecamy wypróbowanie [Instalatora sieci Web programu Visual Studio](https://visualstudio.microsoft.com/downloads), &mdash; który jest małym plikiem, który pozwala na bieżąco korzystać ze wszystkich najnowszych poprawek i funkcji, &mdash; które rozumiemy, że może to nie być możliwe.

::: moniker-end

Na przykład może istnieć zawodne połączenie internetowe lub z niską przepustowością. Jeśli tak, masz kilka opcji: możesz użyć nowej funkcji "Pobierz wszystko, a następnie zainstaluj", aby pobrać pliki przed zainstalowaniem programu, lub możesz użyć wiersza polecenia, aby utworzyć lokalną pamięć podręczną plików.

> [!NOTE]
> Jeśli jesteś administratorem przedsiębiorstwa, który chce wykonać wdrożenie programu Visual Studio w sieci stacji roboczych klienta, które są chronione przez Internet, zapoznaj się z artykułem [Tworzenie instalacji sieciowej programu Visual Studio](../install/create-a-network-installation-of-visual-studio.md) i [Instalowanie certyfikatów wymaganych dla stron instalacji w trybie offline programu Visual Studio](../install/install-certificates-for-visual-studio-offline.md) .

## <a name="use-the-download-all-then-install-feature"></a>Użyj funkcji "Pobierz wszystko, a następnie zainstaluj"

::: moniker range="vs-2017"

[**Nowość w wersji 15,8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): po pobraniu Instalatora sieci Web wybierz opcję Nowy **Pobierz wszystko, a następnie zainstaluj** z Instalator programu Visual Studio. Następnie kontynuuj instalację.

   ![Opcja "Pobierz wszystko, a następnie zainstaluj"](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

Po pobraniu Instalatora sieci Web wybierz opcję Nowy **Pobierz wszystko, a następnie zainstaluj** z Instalator programu Visual Studio. Następnie kontynuuj instalację.

   ![Opcja "Pobierz wszystko, a następnie zainstaluj"](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Zaprojektowano funkcję "Pobierz wszystko, a następnie zainstaluj", aby można było pobrać program Visual Studio jako pojedynczą instalację dla tego samego komputera, na którym został pobrany. Dzięki temu można bezpiecznie rozłączyć się z siecią Web przed zainstalowaniem programu Visual Studio.

> [!IMPORTANT]
> Nie należy używać funkcji "Pobierz wszystko, a następnie zainstaluj", aby utworzyć pamięć podręczną w trybie offline, która ma zostać przetransferowana na inny komputer. Nie została zaprojektowana do pracy w ten sposób. <br><br>Jeśli chcesz utworzyć pamięć podręczną w trybie offline na komputerze lokalnym, którego można użyć do zainstalowania programu Visual Studio, zobacz sekcję [Korzystanie z wiersza polecenia w celu utworzenia lokalnej pamięci podręcznej](#use-the-command-line-to-create-a-local-cache) poniżej.  Alternatywnie strona [Tworzenie instalacji sieciowej programu Visual Studio](../install/create-a-network-installation-of-visual-studio.md) zawiera informacje na temat sposobu tworzenia pamięci podręcznej w sieci.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Tworzenie lokalnej pamięci podręcznej przy użyciu wiersza polecenia
::: moniker range="vs-2017"

Po pobraniu małego programu inicjującego należy użyć wiersza polecenia w celu utworzenia lokalnej pamięci podręcznej. Następnie użyj lokalnej pamięci podręcznej, aby zainstalować program Visual Studio. (Ten proces zastępuje pliki ISO, które były dostępne dla poprzednich wersji). 

::: moniker-end

::: moniker range="vs-2019"

Po pobraniu małego pliku programu inicjującego należy użyć wiersza polecenia w celu utworzenia lokalnej pamięci podręcznej. Następnie użyj lokalnej pamięci podręcznej, aby zainstalować program Visual Studio.

::: moniker-end

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1. Pobieranie programu inicjującego programu Visual Studio

Aby ukończyć ten krok, musisz mieć połączenie z Internetem.

::: moniker range="vs-2017"

Aby uzyskać najnowszy program inicjujący dla programu Visual Studio 2017 w wersji 15,9, przejdź do strony [poprzednich wersji programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) i Pobierz jeden z następujących plików programu inicjującego: 

| Wersja | Nazwa pliku |
|-------------|-----------------------|
|Visual Studio Professional 2017 wersja 15,9 | vs_professional.exe |
|Visual Studio Enterprise 2017 wersja 15,9 | vs_enterprise.exe |
|Visual Studio Build Tools 2017 wersja 15,9  | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Zacznij od pobrania programu inicjującego Visual Studio 2019 ze [strony plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) lub strony wersji programu visual [Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) dla wybranej wersji i wydania programu Visual Studio. Plik Instalatora &mdash; lub program inicjujący &mdash; będzie zgodny z jedną z następujących:

| Wersja                    | Plik                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjującego i chcesz sprawdzić jego wersję. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inicjującego, wybierz polecenie **Właściwości**, wybierz kartę **szczegóły** , a następnie Wyświetl numer **wersji produktu** . Aby dopasować tę liczbę do wersji programu Visual Studio, zapoznaj się ze stroną [numery kompilacji i daty wydania programu Visual Studio](visual-studio-build-numbers-and-release-dates.md) .

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Jeśli wcześniej pobrano plik inicjujący i chcesz sprawdzić jego wersję, poniżej przedstawiono sposób. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inicjującego, wybierz polecenie **Właściwości**, wybierz kartę **szczegóły** , a następnie Wyświetl numer **wersji produktu** . Aby dopasować tę liczbę do wersji programu Visual Studio, zapoznaj się ze stroną [wydań programu Visual studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history) .

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>Krok 2. Tworzenie lokalnej pamięci podręcznej instalacji

Aby ukończyć ten krok, musisz mieć połączenie z Internetem.

Otwórz wiersz polecenia i Użyj parametrów programu inicjującego, zgodnie z definicją w [polecenie Użyj parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) Page w celu utworzenia lokalnej pamięci podręcznej instalacji. Typowe przykłady użycia programu inicjującego w przedsiębiorstwie przedstawiono poniżej i na stronie [przykłady parametrów wiersza polecenia](command-line-parameter-examples.md) . Język inny niż angielski można zainstalować `en-US` , zmieniając ustawienia regionalne z listy ustawień regionalnych [języka](#list-of-language-locales), a także używając [listy składników i obciążeń](workload-and-component-ids.md) , aby dodatkowo dostosować pamięć podręczną.

> [!TIP]
> Aby zapobiec wystąpieniu błędu, upewnij się, że pełna ścieżka instalacji jest krótsza niż 80 znaków.

- W przypadku programu .NET Web i .NET Desktop Development Uruchom polecenie:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- W przypadku programu .NET Desktop i Office Development Uruchom polecenie:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- W przypadku programowania aplikacji klasycznych w języku C++ Uruchom polecenie:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Aby utworzyć pełny układ lokalny, tylko w języku angielskim, przy użyciu wszystkich funkcji (zajmie to dużo czasu na &mdash; _wielu_ funkcjach), uruchom polecenie:

   ```cmd
    vs_enterprise.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Pełny układ programu Visual Studio wymaga co najmniej 35 GB miejsca na dysku. Aby uzyskać więcej informacji, zobacz [wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs/). 

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Pełny układ programu Visual Studio wymaga co najmniej 35 GB miejsca na dysku. Aby uzyskać więcej informacji, zobacz [wymagania systemowe](/visualstudio/releases/2019/system-requirements/).

::: moniker-end


### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3. Instalowanie programu Visual Studio z lokalnej pamięci podręcznej
W przypadku instalowania programu Visual Studio z lokalnej pamięci podręcznej instalacji Instalator programu Visual Studio używa lokalnych wersji plików w pamięci podręcznej. Jednak w przypadku wybrania składników podczas instalacji, które nie znajdują się w pamięci podręcznej, Instalator programu Visual Studio podejmie próbę pobrania ich z Internetu. Aby upewnić się, że instalujesz tylko pobrane pliki, Użyj tych samych [opcji wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md) , które zostały użyte do utworzenia pamięci podręcznej układu. 

Jeśli na przykład utworzono lokalną pamięć podręczną instalacji przy użyciu następującego polecenia:

```cmd
vs_enterprise.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Następnie użyj tego polecenia, aby uruchomić instalację:

```cmd
c:\vslayout\vs_enterprise.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!IMPORTANT]
> Jeśli używasz programu Visual Studio Community, musisz go aktywować, logując się do produktu w ciągu 30 dni od instalacji. Aktywacja wymaga połączenia z Internetem.

> [!NOTE]
> Jeśli zostanie wyświetlony komunikat o błędzie z nieprawidłowym podpisem, należy [zainstalować zaktualizowane certyfikaty](install-certificates-for-visual-studio-offline.md). Otwórz folder certyfikaty w pamięci podręcznej offline. Kliknij dwukrotnie każdy plik certyfikatu, a następnie kliknij przycisk za pomocą kreatora Menedżera certyfikatów. Jeśli zostanie wyświetlony monit o podanie hasła, pozostaw to pole puste.

::: moniker range="vs-2019"
> [!TIP]
> W przypadku instalacji w trybie offline, jeśli zostanie wyświetlony komunikat o błędzie "nie można odnaleźć produktu zgodnego z następującymi parametrami", upewnij się, że używasz `--noweb` przełącznika z wersją 16.3.5 lub nowszą.

::: moniker-end

### <a name="list-of-language-locales"></a>Lista ustawień regionalnych języka

| **Język — ustawienia regionalne** | **Język** |
| ----------------------- | --------------- |
| cs-CZ | Czeski |
| de-DE | Niemiecki |
| en-US | Angielski |
| es-ES | Hiszpański |
| fr-FR | Francuski |
| it-IT | Włoski |
| ja-JP | japoński |
| ko-KR | Koreański |
| pl-PL | Polski |
| pt-BR | Portugalski (Brazylia) |
| ru-RU | Rosyjski |
| tr-TR | Turecki |
| zh-CN | Chiński – uproszczony |
| zh-TW | Chiński – tradycyjny |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Tworzenie instalacji sieciowej programu Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Zainstaluj certyfikaty wymagane do instalacji w trybie offline programu Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
