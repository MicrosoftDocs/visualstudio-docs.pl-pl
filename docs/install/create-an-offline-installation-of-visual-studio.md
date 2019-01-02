---
title: Tworzenie instalacji w trybie offline
description: Dowiedz się, jak zainstalować program Visual Studio w trybie offline, gdy zawodne połączenie z Internetem lub niskiej przepustowości.
ms.date: 08/28/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8359a3b0d96c92a897532edffa7c6ac0b193cd3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952403"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Tworzenie instalacji offline programu Visual Studio 2017

Został zaprojektowany programu Visual Studio 2017 działają poprawnie w kilku różnych konfiguracjach sieci i komputerów. Chociaż zaleca się, że próbujesz [Instalator sieci web programu Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;który to mały plik i pozwala na bieżąco ze wszystkimi najnowsze poprawki i funkcje&mdash;rozumiemy, że użytkownik może okazać się niemożliwe.

Na przykład może być zawodne połączenia internetowego lub taki, który ma o niskiej przepustowości. Jeśli tak, możesz skorzystać z kilku opcji: Można użyć nowej "Pobierz wszystko, a następnie zainstaluj" funkcję, aby pobrać pliki, przed zainstalowaniem lub wiersza polecenia można użyć do utworzenia lokalnej pamięci podręcznej plików.

> [!NOTE]
> Jeśli jesteś administratorem przedsiębiorstwa, który chce wykonać wdrożenie programu Visual Studio 2017 do sieci z stacje robocze klienta, które są zaporą z Internetu, zobacz nasze [Tworzenie instalacji sieciowej programu Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) i [Instalowanie certyfikatów wymaganych do instalacji w trybie offline programu Visual Studio](../install/install-certificates-for-visual-studio-offline.md) stron.

## <a name="use-the-download-all-then-install-feature"></a>Użyj "Pobierz wszystko, a następnie zainstaluj" funkcji

[**Nowość w 15.8**](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017#install
): Po pobraniu Instalatora sieci web, wybierz nową **Pobierz wszystko, a następnie zainstaluj** opcji Instalatora programu Visual Studio. Następnie kontynuuj instalację.

   !["Pobierz wszystko, a następnie zainstaluj" opcja](media/download-all-then-install.png)

## <a name="use-the-command-line-to-create-a-local-cache"></a>Użyj wiersza polecenia, aby utworzyć lokalną pamięć podręczną

Po pobraniu mały program inicjujący, należy użyć wiersza polecenia, aby utworzyć lokalną pamięć podręczną. Następnie należy użyć lokalnej pamięci podręcznej, aby zainstalować program Visual Studio. (Ten proces zastępuje pliki ISO, które były dostępne dla wcześniejszych wersji).

Poniżej przedstawiono sposób.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 — pobieranie program inicjujący programu Visual Studio

Musi mieć połączenie internetowe, aby ukończyć ten krok.

Rozpocznij, pobierając program inicjujący Instalatora programu Visual Studio dla Twojej wybranej wersji programu Visual Studio. Plik Instalatora&mdash;lub program inicjujący&mdash;dopasować, lub być podobne do jednej z następujących czynności.

| Wersja                    | Plik                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

### <a name="step-2---create-a-local-install-cache"></a>Krok 2 — Tworzenie instalacji lokalnej pamięci podręcznej

Musi mieć połączenie internetowe, aby ukończyć ten krok.

> [!IMPORTANT]
> Po zainstalowaniu programu Visual Studio Community 2017, musisz aktywować go w ciągu 30 dni od zainstalowania. Wymaga to dostępu do Internetu.

Otwórz wiersz polecenia i użyj jednego z poleceń w poniższych przykładach. Przykłady, które są wymienione w tym miejscu przyjęto założenie, że korzystasz z wersji Community programu Visual Studio; Dostosuj polecenia odpowiednie dla posiadanej wersji.

- Dla sieci web platformy .NET i programowanie aplikacji klasycznych dla platformy .NET Uruchom polecenie:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- .NET — aplikacje klasyczne i rozwoju pakietu Office Uruchom polecenie:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Do tworzenia klasycznych aplikacji języka C++ Uruchom polecenie:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Aby utworzyć pełną układ lokalnych ze wszystkich funkcji (spowoduje to przejście przez długi czas&mdash;mamy _wiele_ funkcji!), uruchom:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Jeśli chcesz zainstalować język inny niż angielski, zmień `en-US` regionalne z [listę ustawień regionalnych języka](#list-of-language-locales). Następnie należy użyć [listą składników i dostępności obciążeń](workload-and-component-ids.md) dodatkowo dostosować pamięci podręcznej instalacji.

> [!IMPORTANT]
> Pełny układ programu Visual Studio 2017 wymaga co najmniej 35 GB miejsca na dysku i może zająć trochę czasu, aby pobrać. Zobacz [Użyj parametrów wiersza polecenia, aby zainstalować program Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) informacji na temat sposobu tworzenia układu z tylko te składniki, aby zainstalować.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3 — Instalowanie programu Visual Studio z lokalnej pamięci podręcznej

> [!TIP]
> Po uruchomieniu z pamięci podręcznej lokalnej instalacji, Instalator używa lokalnej wersji każdej z tych plików. Jednak jeśli zostanie wybrana podczas instalacji składników, które nie znajdują się w pamięci podręcznej, Instalator podejmuje próbę pobrania ich z Internetu.

Aby upewnić się, instalowania tylko te pliki, które zostały wcześniej pobrane, należy użyć tych samych opcji wiersza polecenia, które zostało użyte do utworzenia pamięci podręcznej układu. Na przykład, jeśli utworzono układ pamięci podręcznej za pomocą następującego polecenia:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Następnie użyj tego polecenia, aby uruchomić instalację:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

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

- [Tworzenie instalacji sieciowej programu Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md)
- [Instalowanie certyfikatów wymaganych do instalacji w trybie offline programu Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 2017 obciążeń i składników identyfikatorów](workload-and-component-ids.md)
