---
title: Rozwiązywanie problemów z instalacją lub uaktualnieniem
description: Czasami elementy mogą być błędne. Jeśli instalacja lub uaktualnienie programu Visual Studio zakończy się niepowodzeniem, ta strona może pomóc.
ms.date: 06/24/2020
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
ms.openlocfilehash: 418cc9f75842cb4f3e9d8c0c0753084e2f0633c2
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350813"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Rozwiązywanie problemów z instalacją i uaktualnieniem programu Visual Studio

> [!IMPORTANT]
> Masz problem z instalacją? Możemy pomóc. Oferujemy opcję obsługi programu [**Chat**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim).

Ten przewodnik rozwiązywania problemów zawiera instrukcje krok po kroku, które powinny rozwiązać większość problemów z instalacją.

## <a name="online-installations"></a>Instalacje online

Poniższe kroki są zoptymalizowane pod kątem typowej instalacji w trybie online. Problem, który ma wpływ na instalację w trybie offline, można znaleźć w artykule [Jak rozwiązywać problemy z instalacją w trybie offline](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Krok 1 — Sprawdź, czy ten problem jest znanym problemem

::: moniker range="vs-2017"

Istnieją pewne znane problemy z Instalator programu Visual Studioem, że firma Microsoft pracuje nad naprawianiem. Aby sprawdzić, czy wystąpił obejście problemu, zapoznaj się [z sekcją znane problemy w informacjach o wersji](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

Istnieją pewne znane problemy z Instalator programu Visual Studioem, że firma Microsoft pracuje nad naprawianiem. Aby sprawdzić, czy wystąpił obejście problemu, zapoznaj się [z sekcją znane problemy w informacjach o wersji](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>Krok 2. próba naprawienia programu Visual Studio

Naprawa rozwiązuje wiele typowych problemów z aktualizacją. Aby uzyskać więcej informacji na temat tego, kiedy i jak używać funkcji naprawy w programie Visual Studio, zobacz temat [Naprawa programu Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>Krok 3. sprawdzenie społeczności deweloperów

Wyszukaj komunikat o błędzie za pomocą [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). Inni członkowie społeczności mogą udokumentować rozwiązanie problemu.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Krok 4. Usuwanie katalogu Instalator programu Visual Studio, aby rozwiązać problemy z uaktualnianiem

Program inicjujący Instalator programu Visual Studio to minimalny lekki plik wykonywalny, który instaluje resztę Instalator programu Visual Studio. Usunięcie Instalator programu Visual Studio plików, a następnie ponowne uruchomienie programu inicjującego może rozwiązać niektóre błędy aktualizacji.

> [!NOTE]
> Wykonanie poniższych czynności powoduje ponowne zainstalowanie plików Instalator programu Visual Studio i zresetowanie metadanych instalacji.

::: moniker range="vs-2017"

1. Zamknij Instalatora programu Visual Studio.
2. Usuń katalog Instalator programu Visual Studio. Zwykle jest to katalog `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Uruchom program inicjujący Instalator programu Visual Studio. Program inicjujący może znajdować się w folderze pobierania z nazwą pliku, która następuje po `vs_[Visual Studio edition]__*.exe` wzorcu. Jeśli nie znajdziesz tej aplikacji, możesz pobrać program inicjujący, przechodząc do strony [pliki do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , a następnie klikając pozycję **Pobierz** dla swojej wersji programu Visual Studio. Następnie uruchom plik wykonywalny, aby zresetować metadane instalacji.
4. Spróbuj ponownie zainstalować lub zaktualizować program Visual Studio. Jeśli Instalator będzie nadal kończyć się niepowodzeniem, przejdź do następnego kroku.

::: moniker-end

::: moniker range="vs-2019"

1. Zamknij Instalatora programu Visual Studio.
2. Usuń katalog Instalator programu Visual Studio. Zwykle jest to katalog `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Uruchom program inicjujący Instalator programu Visual Studio. Program inicjujący może znajdować się w folderze pobierania z nazwą pliku, która następuje po `vs_[Visual Studio edition]__*.exe` wzorcu. Jeśli nie znajdziesz tej aplikacji, możesz pobrać program inicjujący, przechodząc do strony [pliki do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , a następnie klikając pozycję **Pobierz** dla swojej wersji programu Visual Studio. Następnie uruchom plik wykonywalny, aby zresetować metadane instalacji.
4. Spróbuj ponownie zainstalować lub zaktualizować program Visual Studio. Jeśli Instalator będzie nadal kończyć się niepowodzeniem, przejdź do następnego kroku.

::: moniker-end

### <a name="step-5---report-a-problem"></a>Krok 5 — Zgłoś problem

W niektórych sytuacjach, takich jak te powiązane z uszkodzonymi plikami, problemy mogą wymagać przeszukania na zasadzie wielkości liter. Aby pomóc nam Ci pomóc, wykonaj następujące czynności:

::: moniker range="vs-2017"

1. Zbierz dzienniki instalacji. Aby uzyskać szczegółowe informacje [, zobacz Jak pobrać dzienniki instalacji programu Visual Studio](#installation-logs) .
2. Otwórz Instalator programu Visual Studio, a następnie kliknij pozycję **Zgłoś problem** , aby otworzyć narzędzie opinii programu Visual Studio.
![Możesz nawiązać zgodę na przycisk Prześlij opinię, aby otworzyć narzędzie opinii](media/report-a-problem.png)
3. Zgłoś problem z tytułem i podaj odpowiednie szczegóły. Kliknij przycisk **dalej** , aby przejść do sekcji **załączniki** , a następnie dołączyć wygenerowany plik dziennika (zazwyczaj jest to plik `%TEMP%\vslogs.zip` ).
4. Kliknij przycisk **dalej** , aby przejrzeć raport o problemie, a następnie kliknij przycisk **Prześlij**.

::: moniker-end

::: moniker range="vs-2019"

1. Zbierz dzienniki instalacji. Aby uzyskać szczegółowe informacje [, zobacz Jak pobrać dzienniki instalacji programu Visual Studio](#installation-logs) .
2. Otwórz Instalator programu Visual Studio, a następnie kliknij pozycję **Zgłoś problem** , aby otworzyć narzędzie opinii programu Visual Studio.
![Możesz nawiązać zgodę na przycisk Prześlij opinię, aby otworzyć narzędzie opinii](media/vs-2019/vs-installer-report-problem.png)
3. Zgłoś problem z tytułem i podaj odpowiednie szczegóły. Kliknij przycisk **dalej** , aby przejść do sekcji **załączniki** , a następnie dołączyć wygenerowany plik dziennika (zazwyczaj jest to plik `%TEMP%\vslogs.zip` ).
4. Kliknij przycisk **dalej** , aby przejrzeć raport o problemie, a następnie kliknij przycisk **Prześlij**.

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>Krok 6. Uruchamianie InstallCleanup.exe w celu usunięcia plików instalacyjnych

W ostatnim przypadku można [usunąć program Visual Studio](remove-visual-studio.md) , aby usunąć wszystkie pliki instalacyjne i informacje o produkcie.

1. Postępuj zgodnie z instrukcjami w temacie [usuwanie programu Visual Studio](remove-visual-studio.md).
2. Uruchom ponownie program inicjujący opisany w [kroku 4 — Usuń katalog Instalator programu Visual Studio, aby rozwiązać problemy z uaktualnianiem](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Spróbuj ponownie zainstalować lub zaktualizować program Visual Studio.

### <a name="step-7---contact-us-optional"></a>Krok 7. kontakt z nami (opcjonalnie)

Jeśli żaden z poprzednich kroków nie pomoże Ci pomyślnie zainstalować lub uaktualnić programu Visual Studio, skontaktuj się z nami za pomocą opcji obsługi [**czatu na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim), aby uzyskać dalszą pomoc.

## <a name="offline-installations"></a>Instalacje w trybie offline

Poniżej przedstawiono tabelę znanych problemów i niektórych obejść, które mogą pomóc podczas tworzenia [instalacji w trybie offline](create-an-offline-installation-of-visual-studio.md) , a następnie instalacji z układu lokalnego.

| Problem       | Element                   | Rozwiązanie |
| ----------- | ---------------------- | -------- |
| Użytkownicy nie mają dostępu do plików. | uprawnienia (ACL) | Upewnij się, że dostosowujesz uprawnienia (ACL), aby umożliwić im dostęp do odczytu do innych użytkowników *przed* udostępnieniem instalacji w trybie offline. |
| Nie można zainstalować nowych obciążeń, składników lub języków.  | `--layout`  | Upewnij się, że masz dostęp do Internetu, jeśli zainstalujesz program z układu częściowego i wybierzesz obciążenia, składniki lub Języki, które nie zostały pobrane wcześniej w tym układzie częściowym. |

Aby uzyskać więcej informacji na temat rozwiązywania problemów z [instalacją sieciową](create-a-network-installation-of-visual-studio.md), zobacz [Rozwiązywanie problemów związanych z siecią podczas instalowania programu Visual Studio lub korzystania](troubleshooting-network-related-errors-in-visual-studio.md)z niego.

## <a name="installation-logs"></a>Dzienniki instalacji

Dzienniki instalacji są konieczne do rozwiązywania większości problemów z instalacją. Po przesłaniu problemu przy użyciu polecenia [Zgłoś problem](../ide/how-to-report-a-problem-with-visual-studio.md) w Instalator programu Visual Studio te dzienniki zostaną automatycznie uwzględnione w raporcie.

W przypadku kontaktu z usługą pomoc techniczna firmy Microsoft może być konieczne podanie tych dzienników instalacji przy użyciu [Narzędzia do zbierania dzienników Microsoft Visual Studio i .NET Framework](https://www.microsoft.com/download/details.aspx?id=12493). Narzędzie do zbierania dzienników zbiera dzienniki instalacji ze wszystkich składników instalowanych przez program Visual Studio, w tym .NET Framework, Windows SDK i SQL Server. Gromadzi również informacje o komputerze, Instalator Windows spisie i dzienniku zdarzeń systemu Windows dotyczące Instalator programu Visual Studio, Instalator Windows i przywracania systemu.

Aby zebrać dzienniki:

1. [Pobierz narzędzie](https://www.microsoft.com/download/details.aspx?id=12493).
2. Otwórz wiersz polecenia z uprawnieniami administracyjnymi.
3. Uruchom `Collect.exe` z katalogu, w którym zapisano narzędzie.
4. Znajdź otrzymany `vslogs.zip` plik w `%TEMP%` katalogu, na przykład `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` .

> [!NOTE]
> Narzędzie musi być uruchamiane w ramach tego samego konta użytkownika, w ramach którego uruchomiono nieudaną instalację. Jeśli używasz narzędzia z innego konta użytkownika, ustaw `–user:<name>` opcję, aby określić konto użytkownika, na którym uruchomiono nieudaną instalację. Uruchom `Collect.exe -?` polecenie z poziomu wiersza polecenia administratora, aby uzyskać dodatkowe opcje i informacje o użyciu.

## <a name="live-help"></a>Pomoc na żywo

Jeśli rozwiązania wymienione w tym przewodniku rozwiązywania problemów nie pozwalają na pomyślne zainstalowanie lub uaktualnienie programu Visual Studio, Skorzystaj z naszej opcji obsługi [**czatu na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim), aby uzyskać dalszą pomoc.

## <a name="see-also"></a>Zobacz też

* [Napraw program Visual Studio](repair-visual-studio.md)
* [Usuń program Visual Studio](remove-visual-studio.md)
* [Instalowanie i używanie programu Visual Studio i usług platformy Azure za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
