---
title: Tworzenie instalacji w trybie offline
description: Dowiedz się, jak zainstalować program Visual Studio w trybie offline, gdy zawodne połączenie z Internetem lub niskiej przepustowości.
ms.date: 07/24/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 599eef257894c0619252a4c2db23b304e4439d70
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180032"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Tworzenie instalacji w trybie offline programu Visual Studio

::: moniker range="vs-2017"

Został zaprojektowany programu Visual Studio 2017 działają poprawnie w kilku różnych konfiguracjach sieci i komputerów. Chociaż zaleca się, że próbujesz [Instalator sieci web programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)&mdash;który to mały plik i pozwala na bieżąco ze wszystkimi najnowsze poprawki i funkcje&mdash;rozumiemy, że użytkownik może okazać się niemożliwe.

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio 2019 został zaprojektowany tak, aby działał prawidłowo w różnych konfiguracjach sieci i komputerów. Chociaż zaleca się, że próbujesz [Instalator sieci web programu Visual Studio](https://visualstudio.microsoft.com/downloads)&mdash;który to mały plik i pozwala na bieżąco ze wszystkimi najnowsze poprawki i funkcje&mdash;rozumiemy, że użytkownik może okazać się niemożliwe.

::: moniker-end

Na przykład może być zawodne połączenia internetowego lub taki, który ma o niskiej przepustowości. Jeśli tak, masz kilka opcji: Aby pobrać pliki przed zainstalowaniem programu, można użyć nowej funkcji "Pobierz wszystko, a następnie zainstalować" lub użyć wiersza polecenia w celu utworzenia lokalnej pamięci podręcznej plików.

> [!NOTE]
> Jeśli jesteś administratorem przedsiębiorstwa, który chce wykonać wdrożenie programu Visual Studio w sieci stacji roboczych klienta, które są chronione przez Internet, zobacz artykuł [Tworzenie instalacji sieciowej programu Visual Studio](../install/create-a-network-installation-of-visual-studio.md) i [Instalowanie certyfikatów wymagane dla stron instalacji w trybie offline programu Visual Studio](../install/install-certificates-for-visual-studio-offline.md) .

## <a name="use-the-download-all-then-install-feature"></a>Użyj "Pobierz wszystko, a następnie zainstaluj" funkcji

::: moniker range="vs-2017"

[**Nowość w wersji 15,8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): Po pobraniu Instalatora sieci Web wybierz opcję Nowy **Pobierz wszystko, a następnie zainstaluj** z Instalator programu Visual Studio. Następnie kontynuuj instalację.

   !["Pobierz wszystko, a następnie zainstaluj" opcja](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

Po pobraniu Instalatora sieci Web wybierz opcję Nowy **Pobierz wszystko, a następnie zainstaluj** z Instalator programu Visual Studio. Następnie kontynuuj instalację.

   !["Pobierz wszystko, a następnie zainstaluj" opcja](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Zaprojektowano funkcję "Pobierz wszystko, a następnie zainstaluj", aby można było pobrać program Visual Studio jako pojedynczą instalację dla tego samego komputera, na którym został pobrany. Dzięki temu można bezpiecznie rozłączyć się z siecią Web przed zainstalowaniem programu Visual Studio.

> [!IMPORTANT]
> Nie należy używać funkcji "Pobierz wszystko, a następnie zainstaluj", aby utworzyć pamięć podręczną w trybie offline, która ma zostać przetransferowana na inny komputer. Nie została zaprojektowana do pracy w ten sposób. <br><br>Jeśli chcesz utworzyć pamięć podręczną w trybie offline, aby zainstalować program Visual Studio na innym komputerze, zapoznaj się z sekcją [Korzystanie z wiersza polecenia w celu utworzenia lokalnej pamięci](#use-the-command-line-to-create-a-local-cache) podręcznej tej strony, aby uzyskać informacje na temat sposobu tworzenia lokalnej pamięci podręcznej lub [tworzenia instalacji sieciowej programu Visual ](../install/create-a-network-installation-of-visual-studio.md)Na stronie Studio znajduje się więcej informacji na temat tworzenia pamięci podręcznej sieci.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Użyj wiersza polecenia, aby utworzyć lokalną pamięć podręczną

Po pobraniu mały program inicjujący, należy użyć wiersza polecenia, aby utworzyć lokalną pamięć podręczną. Następnie należy użyć lokalnej pamięci podręcznej, aby zainstalować program Visual Studio. (Ten proces zastępuje pliki ISO, które były dostępne dla wcześniejszych wersji).

Poniżej przedstawiono sposób.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 — pobieranie program inicjujący programu Visual Studio

Musi mieć połączenie internetowe, aby ukończyć ten krok.

Rozpocznij, pobierając program inicjujący Instalatora programu Visual Studio dla Twojej wybranej wersji programu Visual Studio. Plik Instalatora&mdash;lub program inicjujący&mdash;dopasować, lub być podobne do jednej z następujących czynności.

::: moniker range="vs-2017"

| Wersja                    | Plik                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

::: moniker-end

::: moniker range="vs-2019"

| Wersja                    | Plik                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>Krok 2 — Tworzenie instalacji lokalnej pamięci podręcznej

Musi mieć połączenie internetowe, aby ukończyć ten krok.

> [!IMPORTANT]
> W przypadku instalowania programu Visual Studio Community należy aktywować go w ciągu 30 dni od instalacji. Wymaga to dostępu do Internetu.

Otwórz wiersz polecenia i użyj jednego z poleceń w poniższych przykładach. Przykłady, które są wymienione w tym miejscu przyjęto założenie, że korzystasz z wersji Community programu Visual Studio; Dostosuj polecenia odpowiednie dla posiadanej wersji.

> [!TIP]
> Aby zapobiec wystąpieniu błędu, upewnij się, że pełna ścieżka instalacji jest krótsza niż 80 znaków.

- Dla sieci web platformy .NET i programowanie aplikacji klasycznych dla platformy .NET Uruchom polecenie:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- .NET — aplikacje klasyczne i rozwoju pakietu Office Uruchom polecenie:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Do tworzenia klasycznych aplikacji języka C++ Uruchom polecenie:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Aby utworzyć pełną układ lokalnych ze wszystkich funkcji (spowoduje to przejście przez długi czas&mdash;mamy _wiele_ funkcji!), uruchom:

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Pełny układ programu Visual Studio wymaga co najmniej 35 GB miejsca na dysku. Aby uzyskać więcej informacji, zobacz [wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs/). Aby uzyskać informacje na temat sposobu tworzenia układu tylko z składnikami, które chcesz zainstalować, zobacz [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Pełny układ programu Visual Studio wymaga co najmniej 35 GB miejsca na dysku. Aby uzyskać więcej informacji, zobacz [wymagania systemowe](/visualstudio/releases/2019/system-requirements/). Aby uzyskać informacje na temat sposobu tworzenia układu tylko z składnikami, które chcesz zainstalować, zobacz [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

Jeśli chcesz zainstalować język inny niż angielski, zmień `en-US` regionalne z [listę ustawień regionalnych języka](#list-of-language-locales). Następnie należy użyć [listą składników i dostępności obciążeń](workload-and-component-ids.md) dodatkowo dostosować pamięci podręcznej instalacji.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3 — Instalowanie programu Visual Studio z lokalnej pamięci podręcznej

> [!TIP]
> Po uruchomieniu z pamięci podręcznej lokalnej instalacji, Instalator używa lokalnej wersji każdej z tych plików. Jednak jeśli zostanie wybrana podczas instalacji składników, które nie znajdują się w pamięci podręcznej, Instalator podejmuje próbę pobrania ich z Internetu.

Aby upewnić się, instalowania tylko te pliki, które zostały wcześniej pobrane, należy użyć tych samych opcji wiersza polecenia, które zostało użyte do utworzenia pamięci podręcznej układu. Na przykład, jeśli utworzono układ pamięci podręcznej za pomocą następującego polecenia:

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Następnie użyj tego polecenia, aby uruchomić instalację:

```cmd
c:\vslayout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!NOTE]
> Jeśli wystąpi błąd, że podpis jest nieprawidłowy, należy zainstalować zaktualizowane certyfikaty. Otwórz folder certyfikatów w pamięci podręcznej w trybie offline. Kliknij dwukrotnie plik certyfikatu, a następnie kliknij za pomocą Kreatora Menedżera certyfikatów. Jeśli zostanie wyświetlony monit o podanie hasła, pozostaw to pole puste.

### <a name="list-of-language-locales"></a>Listę ustawień regionalnych języka

| **Ustawienia regionalne na język** | **Język** |
| ----------------------- | --------------- |
| cs-CZ | czeski |
| de-DE. | niemiecki |
| en-US | Angielski |
| es-ES | Hiszpański |
| fr-FR | Francuski |
| IT-IT | Włoski |
| ja-JP | japoński |
| ko-KR | koreański |
| pl-PL | polski |
| pt-BR | Portugalski (Brazylia) |
| ru-RU | Rosyjski |
| tr-TR | turecki |
| zh-CN | Chiński (uproszczony) |
| zh-TW | Chiński — tradycyjny |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

- [Tworzenie instalacji sieciowej programu Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Instalowanie certyfikatów wymaganych do instalacji w trybie offline programu Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
