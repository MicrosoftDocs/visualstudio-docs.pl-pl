---
title: Rozwiązywanie problemów z instalacją lub uaktualnieniem
description: Czasami coś może pójść nie tak. Jeśli instalacja lub uaktualnienie programu Visual Studio nie powiedzie się, ta strona może pomóc.
ms.date: 09/13/2019
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9dfdf504378dafd7d71288cae1927dd8d6bb9e56
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114997"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Rozwiązywanie problemów z instalacją i uaktualnianiem programu Visual Studio

> [!IMPORTANT]
> Masz problem z instalacją? Możemy pomóc. Oferujemy opcję wsparcia [**czatu na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim).

Ten przewodnik rozwiązywania problemów zawiera instrukcje krok po kroku, które powinny rozwiązać większość problemów z instalacją.

## <a name="online-installations"></a>Instalacje online

Poniższe kroki są zoptymalizowane pod kątem typowej instalacji online. Aby uzyskać problem dotyczący instalacji w trybie offline, zobacz [Jak rozwiązać problem z instalacją w trybie offline](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Krok 1 - Sprawdź, czy ten problem jest znany

::: moniker range="vs-2017"

Istnieją pewne znane problemy z Instalatorem programu Visual Studio, który firma Microsoft pracuje nad naprawianiem. Aby sprawdzić, czy istnieje obejście problemu, zapoznaj się [z sekcją Znane problemy w naszych informacjach o wersji](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

Istnieją pewne znane problemy z Instalatorem programu Visual Studio, który firma Microsoft pracuje nad naprawianiem. Aby sprawdzić, czy istnieje obejście problemu, zapoznaj się [z sekcją Znane problemy w naszych informacjach o wersji](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---check-with-the-developer-community"></a>Krok 2 - Skontaktuj się ze społecznością programistów

Wyszukaj komunikat o błędzie w [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). Inni członkowie społeczności mogli udokumentować rozwiązanie problemu.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Krok 3 - Usuwanie katalogu instalatora programu Visual Studio w celu rozwiązania problemów z uaktualnieniem

Program inikuscyjny instalatora programu Visual Studio jest minimalnym lekkim plikiem wykonywalnym, który instaluje pozostałą część instalatora programu Visual Studio. Usuwanie plików Instalatora programu Visual Studio, a następnie ponowne uruchamianie programu inichowania może rozwiązać niektóre błędy aktualizacji.

> [!NOTE]
> Wykonywanie następujących akcji ponownie instaluje pliki Instalatora programu Visual Studio i resetuje metadane instalacji.

::: moniker range="vs-2017"

1. Zamknij Instalatora programu Visual Studio.
2. Usuń katalog Instalatora programu Visual Studio. Zazwyczaj katalog jest `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Uruchom program uruchamiający instalator programu Visual Studio. Program initrapper może znajdować się w folderze Pobrane z nazwą pliku, która jest zgodna ze wzorcem. `vs_[Visual Studio edition]__*.exe` Jeśli nie znajdziesz tej aplikacji, możesz pobrać program inikusingowy, przechodząc do strony [pobierania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) i klikając pozycję **Pobierz** dla swojej wersji programu Visual Studio. Następnie uruchom plik wykonywalny, aby zresetować metadane instalacji.
4. Spróbuj ponownie zainstalować lub zaktualizować program Visual Studio. Jeśli Instalator nadal zakończy się niepowodzeniem, przejdź do następnego kroku.

::: moniker-end

::: moniker range="vs-2019"

1. Zamknij Instalatora programu Visual Studio.
2. Usuń katalog Instalatora programu Visual Studio. Zazwyczaj katalog jest `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Uruchom program uruchamiający instalator programu Visual Studio. Program initrapper może znajdować się w folderze Pobrane z nazwą pliku, która jest zgodna ze wzorcem. `vs_[Visual Studio edition]__*.exe` Jeśli nie znajdziesz tej aplikacji, możesz pobrać program inikusingowy, przechodząc do strony [pobierania programu Visual Studio](https://visualstudio.microsoft.com/downloads) i klikając pozycję **Pobierz** dla swojej wersji programu Visual Studio. Następnie uruchom plik wykonywalny, aby zresetować metadane instalacji.
4. Spróbuj ponownie zainstalować lub zaktualizować program Visual Studio. Jeśli Instalator nadal zakończy się niepowodzeniem, przejdź do następnego kroku.

::: moniker-end

### <a name="step-4---report-a-problem"></a>Krok 4 - Zgłoś problem

W niektórych sytuacjach, takich jak te związane z uszkodzonymi plikami, problemy mogą być analizowane indywidualnie. Aby pomóc nam pomóc, wykonaj następujące czynności:

::: moniker range="vs-2017"

1. Zbieraj dzienniki konfiguracji. Zobacz [Jak uzyskać dzienniki instalacji programu Visual Studio, aby](#installation-logs) uzyskać szczegółowe informacje.
2. Otwórz Instalatora programu Visual Studio, a następnie kliknij pozycję **Zgłoś problem,** aby otworzyć narzędzie Visual Studio Feedback.
![Możesz przejść na kartę do przycisku Przekaż opinię, aby otworzyć narzędzie opinii](media/report-a-problem.png)
3. Nadaj tytułowi raportu problemu i podaj odpowiednie szczegóły. Kliknij **przycisk Dalej,** aby przejść do sekcji **Załączniki,** a następnie dołącz `%TEMP%\vslogs.zip`wygenerowany plik dziennika (zazwyczaj plik znajduje się w ).
4. Kliknij **przycisk Dalej,** aby przejrzeć raport o problemie, a następnie kliknij przycisk **Prześlij**.

::: moniker-end

::: moniker range="vs-2019"

1. Zbieraj dzienniki konfiguracji. Zobacz [Jak uzyskać dzienniki instalacji programu Visual Studio, aby](#installation-logs) uzyskać szczegółowe informacje.
2. Otwórz Instalatora programu Visual Studio, a następnie kliknij pozycję **Zgłoś problem,** aby otworzyć narzędzie Visual Studio Feedback.
![Możesz przejść na kartę do przycisku Przekaż opinię, aby otworzyć narzędzie opinii](media/vs-2019/vs-installer-report-problem.png)
3. Nadaj tytułowi raportu problemu i podaj odpowiednie szczegóły. Kliknij **przycisk Dalej,** aby przejść do sekcji **Załączniki,** a następnie dołącz `%TEMP%\vslogs.zip`wygenerowany plik dziennika (zazwyczaj plik znajduje się w ).
4. Kliknij **przycisk Dalej,** aby przejrzeć raport o problemie, a następnie kliknij przycisk **Prześlij**.

::: moniker-end

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Krok 5 - Uruchom InstallCleanup.exe, aby usunąć pliki instalacyjne

W ostateczności można [usunąć program Visual Studio,](remove-visual-studio.md) aby usunąć wszystkie pliki instalacyjne i informacje o produkcie.

1. Postępuj zgodnie z instrukcjami w [umykać program Visual Studio](remove-visual-studio.md).
2. Uruchom ponownie program uruchamiający, który jest opisany w [kroku 3 — usuń katalog Instalatora programu Visual Studio, aby rozwiązać problemy z uaktualnieniem](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Spróbuj ponownie zainstalować lub zaktualizować program Visual Studio.

### <a name="step-6---contact-us-optional"></a>Krok 6 - Skontaktuj się z nami (opcjonalnie)

Jeśli żaden z poprzednich kroków nie pomoże Ci pomyślnie zainstalować lub uaktualnić programu Visual Studio, skontaktuj się z nami, korzystając z naszej opcji pomocy technicznej [**czatu na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim), aby uzyskać dalszą pomoc.

## <a name="offline-installations"></a>Instalacje w trybie offline

Oto tabela znanych problemów i niektórych obejść, które mogą pomóc podczas tworzenia [instalacji w trybie offline,](create-an-offline-installation-of-visual-studio.md) a następnie zainstalować z układu lokalnego.

| Problem       | Element                   | Rozwiązanie |
| ----------- | ---------------------- | -------- |
| Użytkownicy nie mają dostępu do plików. | uprawnienia (listy ACL) | Upewnij się, że można dostosować uprawnienia (Listy ACL), tak aby udzielić dostępu do odczytu innym użytkownikom *przed* udostępnieniem instalacji w trybie offline. |
| Nowe obciążenia, składniki lub języki nie można zainstalować.  | `--layout`  | Upewnij się, że masz dostęp do Internetu, jeśli instalujesz z układu częściowego i wybierzesz obciążenia, składniki lub języki, które nie zostały pobrane wcześniej w tym układzie częściowym. |

Aby uzyskać więcej informacji na temat rozwiązywania problemów z [instalacją sieciową,](create-a-network-installation-of-visual-studio.md)zobacz [Rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania programu Visual Studio lub korzystania z niego](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Dzienniki instalacji

Dzienniki instalacji są potrzebne do rozwiązywania większości problemów z instalacją. Po przesłaniu problemu przy użyciu [zgłoś problem](../ide/how-to-report-a-problem-with-visual-studio.md) w Instalatorze programu Visual Studio, te dzienniki są automatycznie uwzględniane w raporcie.

Jeśli skontaktujesz się z pomocą techniczną firmy Microsoft, może być konieczne podanie tych dzienników konfiguracji przy użyciu [narzędzia Microsoft Visual Studio i .NET Framework Log Collection Tool](https://www.microsoft.com/download/details.aspx?id=12493). Narzędzie do zbierania dzienników zbiera dzienniki konfiguracji ze wszystkich składników zainstalowanych przez program Visual Studio, w tym .NET Framework, Windows SDK i SQL Server. Zbiera również informacje o komputerze, spisie Instalatora Windows i informacje o dzienniku zdarzeń systemu Windows dla Instalatora programu Visual Studio, Instalatora Windows i przywracania systemu.

Aby zebrać dzienniki:

1. [Pobierz narzędzie](https://www.microsoft.com/download/details.aspx?id=12493).
2. Otwórz wiersz polecenia administracyjnego.
3. Uruchom `Collect.exe` z katalogu, w którym zapisana jest narzędzie.
4. Znajdź wynikowy `vslogs.zip` plik `%TEMP%` w katalogu, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`na przykład .

> [!NOTE]
> Narzędzie musi być uruchamiane na tym samym koncie użytkownika, pod które została uruchomiona nieudana instalacja. Jeśli narzędzie jest uruchomione z innego konta `–user:<name>` użytkownika, należy ustawić opcję określania konta użytkownika, na którym została uruchomiona instalacja, w ramach której nie powiodła się instalacja. Uruchom `Collect.exe -?` z wiersza polecenia administratora, aby uzyskać dodatkowe opcje i informacje o użytkowaniu.

## <a name="live-help"></a>Pomoc na żywo

Jeśli rozwiązania wymienione w tym przewodniku rozwiązywania problemów nie pomagają w pomyślnym zainstalowaniu lub uaktualnieniu programu Visual Studio, skorzystaj z naszej opcji pomocy technicznej [**na czacie na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim), aby uzyskać dalszą pomoc.

## <a name="see-also"></a>Zobacz też

* [Usuwanie programu Visual Studio](remove-visual-studio.md)
* [Instalowanie i używanie programów Visual Studio i usług Platformy Azure za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Przewodnik dla administratora programu Visual Studio](visual-studio-administrator-guide.md)
