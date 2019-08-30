---
title: Rozwiązywanie problemów z instalacją lub Uaktualnij problemów
description: Czasami mogą wystąpić problemy. Jeśli Twoje instalację programu Visual Studio lub uaktualnienie nie powiedzie się, może pomóc tej strony.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fbecfb7e74b38bb935414e701618cef361bf0506
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180022"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Rozwiązywanie problemów z instalacją i uaktualnieniem programu Visual Studio

> [!IMPORTANT]
> Nie, problemów z instalacją? Możemy pomóc. Firma Microsoft oferuje [ **Czat na żywo** ](https://visualstudio.microsoft.com/vs/support/#talktous) opcję pomocy technicznej (tylko w języku angielskim).

Ten przewodnik rozwiązywania problemów zawiera instrukcje krok po kroku, które należy rozwiązać większość problemów z instalacją.

## <a name="how-to-troubleshoot-an-online-installation"></a>Jak rozwiązywać problemy z instalacji w trybie online

Poniższe kroki są zoptymalizowane pod kątem typowej instalacji w trybie online. Problem, który ma wpływ na instalacji w trybie offline, zobacz [rozwiązywania problemów z instalacją w trybie offline](#how-to-troubleshoot-an-offline-installation).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Krok 1. Sprawdź, czy ten problem jest znany problem

::: moniker range="vs-2017"

Istnieją znane problemy za pomocą Instalatora programu Visual Studio, firma Microsoft pracuje nad rozwiązaniem problemu. Aby sprawdzić, czy istnieje obejście dla danego problemu, sprawdź [sekcji Znane problemy w naszych informacjach](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

Istnieją znane problemy za pomocą Instalatora programu Visual Studio, firma Microsoft pracuje nad rozwiązaniem problemu. Aby sprawdzić, czy istnieje obejście dla danego problemu, sprawdź [sekcji Znane problemy w naszych informacjach](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---check-with-the-developer-community"></a>Krok 2 — skontaktuj się z społeczność deweloperów

Wyszukiwanie w sieci komunikat o błędzie z [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). Inni członkowie społeczności mogą mieć udokumentowane rozwiązanie problemu.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Krok 3 — Usuń katalog Instalatora programu Visual Studio, aby rozwiązać problemy z uaktualnianiem

Program inicjujący Instalatora programu Visual Studio jest minimalny plik wykonywalny lekki, który instaluje pozostałą część Instalatora programu Visual Studio. Usuwanie plików Instalatora programu Visual Studio, a następnie ponowne uruchomienie program inicjujący może rozwiązać niektóre błędy aktualizacji.

> [!NOTE]
> Wykonując następujące czynności ponownie instaluje pliki Instalatora programu Visual Studio i resetuje metadanych instalacji.

::: moniker range="vs-2017"

1. Zamknij Instalatora programu Visual Studio.
2. Usuń katalog Instalatora programu Visual Studio. Zazwyczaj jest katalog `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Uruchom program inicjujący Instalatora programu Visual Studio. Program inicjujący można znaleźć w folderze pobrane przy użyciu nazwy pliku, który następuje po `vs_[Visual Studio edition]__*.exe` wzorca. Jeśli nie możesz znaleźć tę aplikację, możesz pobrać program inicjujący, przechodząc do [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony i klikając **Pobierz** używanej wersji programu Visual Studio. Następnie uruchom plik wykonywalny, aby zresetować metadane instalacji.
4. Spróbuj zainstalować lub zaktualizować program Visual Studio ponownie. Jeśli Instalator zakończy się niepowodzeniem, przejdź do następnego kroku.

::: moniker-end

::: moniker range="vs-2019"

1. Zamknij Instalatora programu Visual Studio.
2. Usuń katalog Instalatora programu Visual Studio. Zazwyczaj jest katalog `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Uruchom program inicjujący Instalatora programu Visual Studio. Program inicjujący można znaleźć w folderze pobrane przy użyciu nazwy pliku, który następuje po `vs_[Visual Studio edition]__*.exe` wzorca. Jeśli nie możesz znaleźć tę aplikację, możesz pobrać program inicjujący, przechodząc do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony i klikając **Pobierz** używanej wersji programu Visual Studio. Następnie uruchom plik wykonywalny, aby zresetować metadane instalacji.
4. Spróbuj zainstalować lub zaktualizować program Visual Studio ponownie. Jeśli Instalator zakończy się niepowodzeniem, przejdź do następnego kroku.

::: moniker-end

### <a name="step-4---report-a-problem"></a>Krok 4 — informacje o problemie

W niektórych sytuacjach, takich jak powiązane z uszkodzonych plików problemy, być może trzeba rozważyć w przypadku przez. Aby pomóc nam sobie pomóc, wykonaj następujące czynności:

::: moniker range="vs-2017"

1. Zbieranie dzienników instalacji. Zobacz [jak uzyskać dzienniki instalacji programu Visual Studio](#how-to-get-visual-studio-installation-logs) Aby uzyskać szczegółowe informacje.
2. Otwórz Instalatora programu Visual Studio, a następnie kliknij przycisk **Zgłoś problem** można otworzyć narzędzia Visual Studio opinii.
![Ustawić tabulator, aby przycisk Podaj opinię, aby otworzyć narzędzie opinii](media/report-a-problem.png)
3. Nadaj tytuł raport o problemie i podaj odpowiednie szczegóły. Kliknij przycisk **dalej** można przejść do **załączniki** sekcji, a następnie dołącz plik dziennika wygenerowany (zazwyczaj plik znajduje się w `%TEMP%\vslogs.zip`).
4. Kliknij przycisk **dalej** Przejrzyj raport o problemie, a następnie kliknij przycisk **przesyłania**.

::: moniker-end

::: moniker range="vs-2019"

1. Zbieranie dzienników instalacji. Zobacz [jak uzyskać dzienniki instalacji programu Visual Studio](#how-to-get-visual-studio-installation-logs) Aby uzyskać szczegółowe informacje.
2. Otwórz Instalatora programu Visual Studio, a następnie kliknij przycisk **Zgłoś problem** można otworzyć narzędzia Visual Studio opinii.
![Ustawić tabulator, aby przycisk Podaj opinię, aby otworzyć narzędzie opinii](media/vs-2019/vs-installer-report-problem.png)
3. Nadaj tytuł raport o problemie i podaj odpowiednie szczegóły. Kliknij przycisk **dalej** można przejść do **załączniki** sekcji, a następnie dołącz plik dziennika wygenerowany (zazwyczaj plik znajduje się w `%TEMP%\vslogs.zip`).
4. Kliknij przycisk **dalej** Przejrzyj raport o problemie, a następnie kliknij przycisk **przesyłania**.

::: moniker-end

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Krok 5 — InstallCleanup.exe przebiegu można usunąć plików instalacyjnych

W ostateczności możesz [usunąć program Visual Studio](remove-visual-studio.md) usunąć wszystkie pliki instalacyjne i informacje o produkcie.

1. Postępuj zgodnie z instrukcjami w [usunięcie programu Visual Studio](remove-visual-studio.md).
2. Uruchom ponownie program inicjujący, który jest opisany w [krok 3 — Delete katalogu Instalatora programu Visual Studio, aby rozwiązać problemy z uaktualnianiem](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Spróbuj zainstalować lub zaktualizować program Visual Studio ponownie.

### <a name="step-6---contact-us-optional"></a>Krok 6 — skontaktuj się z nami (opcjonalnie)

Jeśli żaden z poprzednich kroków należy postępować instalacja lub uaktualnienie programu Visual Studio, skontaktuj się z nami za pomocą naszych [ **Czat na żywo** ](https://visualstudio.microsoft.com/vs/support/#talktous) obsługuje opcji (tylko w języku angielskim), aby uzyskać dalszą pomoc.

## <a name="how-to-troubleshoot-an-offline-installation"></a>Jak rozwiązywać problemy z instalacji w trybie offline

W tym miejscu znajduje się tabela znane problemy i obejścia, które mogą być pomocne podczas instalacji z układu lokalnego.

| Problem       | Element                   | Rozwiązanie |
| ----------- | ---------------------- | -------- |
| Użytkownicy nie mają dostępu do plików. | uprawnienia (kontroli dostępu ACL) | Upewnij się, dostosowanie uprawnień (kontroli dostępu ACL), tak aby ich przyznawać innym użytkownikom dostęp do odczytu *przed* udostępnianie instalacji w trybie offline. |
| Nowych obciążeń i składników oraz języki, instalacja zakończyć się niepowodzeniem.  | `--layout`  | Upewnij się, że masz dostęp do Internetu, jeśli instalacji z układu częściowe i wybierz obciążeń, składniki oraz języki, które nie zostały pobrane wcześniej w tym układzie częściowe. |

## <a name="how-to-get-visual-studio-installation-logs"></a>Jak uzyskać dzienniki instalacji programu Visual Studio

Dzienniki instalacji są wymagane do większości rozwiązywania problemów z instalacją. Gdy Prześlij problem za pomocą [Zgłoś Problem](../ide/how-to-report-a-problem-with-visual-studio.md) w Instalatorze programu Visual Studio, te dzienniki są automatycznie uwzględniane w raporcie.

Jeśli zamierzasz zgłosić Support firmy Microsoft, może być konieczne dostarczenie tych dzienników instalacji przy użyciu [Microsoft Visual Studio i narzędzia do zbierania dzienników platformy .NET Framework](https://aka.ms/vscollect). Narzędzie do zbierania dzienników zbiera dzienniki instalacji ze wszystkich składników instalowanych przez program Visual Studio, w tym .NET Framework, Windows SDK i SQL Server. Zbiera także informacje o komputerze, spis dla Instalatora Windows i Windows informacje dziennika zdarzeń dla Instalatora programu Visual Studio, Instalator Windows i przywracanie systemu.

Aby zebrać dzienniki:

1. [Pobierz narzędzie](https://aka.ms/vscollect).
2. Otwórz administracyjny wiersz polecenia.
3. Uruchom `Collect.exe` z katalogu, w którym to narzędzie zostało zapisane.
4. Znajdź wartość wynikowa `vslogs.zip` plików w Twojej `%TEMP%` katalogu, na przykład `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> Narzędzie musi działać w ramach tego samego konta użytkownika w obszarze uruchomiona została Nieudana instalacja. Jeśli uruchamiasz narzędzie z innego konta użytkownika, ustaw `–user:<name>` opcję, aby określić konto użytkownika w ramach której zostało uruchomione nieudanej instalacji. Uruchom `Collect.exe -?` w wierszu polecenia administratora, aby uzyskać dodatkowe informacje dotyczące opcji i użycia.

## <a name="get-live-help"></a>Uzyskaj pomoc na żywo

Jeśli te rozwiązania wymienione w tym przewodniku rozwiązywania problemów nie pomogą pomyślnie zainstalować lub uaktualnić programu Visual Studio, użyj naszych [ **Czat na żywo** ](https://visualstudio.microsoft.com/vs/support/#talktous) obsługuje opcji (tylko w języku angielskim), aby uzyskać dalszą pomoc.

## <a name="see-also"></a>Zobacz także

* [Usuń program Visual Studio](remove-visual-studio.md)
* [Instalowanie i używanie programu Visual Studio i usług platformy Azure za serwerem zapory lub serwera proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
