---
title: Rozwiązywanie problemów z instalacją lub uaktualnieniem
description: Czasami coś może pójść nie tak. Jeśli instalacja Visual Studio lub uaktualnienie nie powiedzie się, ta strona może pomóc.
ms.date: 06/24/2020
ms.custom: acquisition
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3d7dfacf00dbbb37946e4eaa8f1feb89b4059103
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112470"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Rozwiązywanie Visual Studio instalacji i uaktualniania

> [!IMPORTANT]
> Masz problem z instalacją? Możemy ci pomóc. Oferujemy opcję pomocy [**technicznej dla czatu instalacyjnego**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim).

Ten przewodnik rozwiązywania problemów zawiera instrukcje krok po kroku, które powinny rozwiązać większość problemów z instalacją.

## <a name="online-installations"></a>Instalacje online

Poniższe kroki są zoptymalizowane pod kątem typowej instalacji online. W przypadku problemu, który ma wpływ na instalację w trybie offline, zobacz [Jak rozwiązywać problemy z instalacją w trybie offline.](#offline-installations)

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Krok 1. Sprawdzanie, czy ten problem jest znany

::: moniker range="vs-2017"

Istnieją znane problemy z błędami, Instalator programu Visual Studio nad ich rozwiązaniem pracuje firma Microsoft. Aby sprawdzić, czy istnieje obejście problemu, zapoznaj się z sekcją Znane problemy [w informacjach o wersji](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

Istnieją znane problemy z błędami, Instalator programu Visual Studio nad ich rozwiązaniem pracuje firma Microsoft. Aby sprawdzić, czy istnieje obejście problemu, zapoznaj się z sekcją Znane problemy [w informacjach o wersji](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>Krok 2— Spróbuj naprawić Visual Studio

Naprawa rozwiązuje wiele typowych problemów z aktualizacjami. Aby uzyskać więcej informacji na temat tego, kiedy i jak używać funkcji naprawy w programie Visual Studio, zobacz [Repair Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>Krok 3. Skontaktuj się ze społecznością deweloperów

Wyszukaj komunikat o błędzie za pomocą [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8). Inni członkowie społeczności mogli udokumentować rozwiązanie Twojego problemu.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Krok 4 . Usuwanie Instalator programu Visual Studio, aby rozwiązać problemy z uaktualnieniem

Program Instalator programu Visual Studio inicjujący to minimalny lekki plik wykonywalny, który instaluje pozostałą część Instalator programu Visual Studio. Usunięcie Instalator programu Visual Studio plików, a następnie ponowne uruchomienie programu inicjjącego może rozwiązać niektóre błędy aktualizacji.

> [!NOTE]
> Wykonanie następujących akcji powoduje ponowne zainstalowanie Instalator programu Visual Studio plików i zresetowanie metadanych instalacji.

::: moniker range="vs-2017"

1. Zamknij Instalatora programu Visual Studio.
2. Usuń Instalator programu Visual Studio katalogu. Zazwyczaj katalog to `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Uruchom Instalator programu Visual Studio inicjujący. Program inicjujący może znaleźć się w folderze Pobrane z nazwą pliku zgodną ze `vs_[Visual Studio edition]__*.exe` wzorcem. Jeśli nie znajdziesz tej aplikacji, możesz pobrać program inicjujący, przechodząc do  strony pobierania aplikacji [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) i klikając pozycję Pobierz dla swojej wersji Visual Studio. Następnie uruchom plik wykonywalny, aby zresetować metadane instalacji.
4. Spróbuj zainstalować lub zaktualizować Visual Studio ponownie. Jeśli instalator nadal nie powiedzie się, przejdź do następnego kroku.

::: moniker-end

::: moniker range="vs-2019"

1. Zamknij Instalatora programu Visual Studio.
2. Usuń Instalator programu Visual Studio katalogu. Zazwyczaj katalog to `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Uruchom Instalator programu Visual Studio inicjujący. Program inicjujący może znaleźć się w folderze Pobrane z nazwą pliku zgodną ze `vs_[Visual Studio edition]__*.exe` wzorcem. Jeśli nie znajdziesz tej aplikacji, możesz pobrać program inicjujący, przechodząc do  strony pobierania aplikacji [Visual Studio](https://visualstudio.microsoft.com/downloads) i klikając pozycję Pobierz dla swojej wersji Visual Studio. Następnie uruchom plik wykonywalny, aby zresetować metadane instalacji.
4. Spróbuj zainstalować lub zaktualizować Visual Studio ponownie. Jeśli instalator nadal nie powiedzie się, przejdź do następnego kroku.

::: moniker-end

### <a name="step-5---report-a-problem"></a>Krok 5. Zgłaszanie problemu

W niektórych sytuacjach, takich jak te związane z uszkodzonymi plikami, problemy mogą być analizowane wielokrotnie. Aby nam pomóc, wykonaj następujące czynności:

::: moniker range="vs-2017"

1. Zbierz dzienniki instalacji. Aby [uzyskać szczegółowe informacje, zobacz Visual Studio dziennika](#installation-logs) instalacji aplikacji.
2. Otwórz Instalator programu Visual Studio, a następnie kliknij pozycję Zgłoś **problem,** aby otworzyć Visual Studio opinie.
![Możesz nacisnąć klawisz Tab na przycisku Udostępnij opinię, aby otworzyć narzędzie do opinii](media/report-a-problem.png)
3. Nadaj tytuł raportowi problemu i podaj odpowiednie szczegóły. Kliknij **przycisk** Dalej, aby przejść do **sekcji Załączniki,** a następnie dołączyć wygenerowany plik dziennika (zazwyczaj plik znajduje się w pliku `%TEMP%\vslogs.zip` ).
4. Kliknij **przycisk Dalej,** aby przejrzeć raport o problemie, a następnie kliknij pozycję **Prześlij.**

::: moniker-end

::: moniker range="vs-2019"

1. Zbierz dzienniki instalacji. Aby [uzyskać szczegółowe informacje, zobacz Visual Studio dziennika](#installation-logs) instalacji aplikacji.
2. Otwórz Instalator programu Visual Studio, a następnie kliknij pozycję Zgłoś **problem,** aby otworzyć Visual Studio opinie.
![Możesz nacisnąć klawisz Tab na przycisku Udostępnij opinię, aby otworzyć narzędzie do opinii](media/vs-2019/vs-installer-report-problem.png)
3. Nadaj tytuł raportowi problemu i podaj odpowiednie szczegóły. Kliknij **przycisk** Dalej, aby przejść do **sekcji Załączniki,** a następnie dołączyć wygenerowany plik dziennika (zazwyczaj plik znajduje się w pliku `%TEMP%\vslogs.zip` ).
4. Kliknij **przycisk Dalej,** aby przejrzeć raport o problemie, a następnie kliknij pozycję **Prześlij.**

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>Krok 6. Uruchamianie InstallCleanup.exe w celu usunięcia plików instalacyjnych

W ostateczności możesz usunąć [Visual Studio,](remove-visual-studio.md) aby usunąć wszystkie pliki instalacyjne i informacje o produkcie.

1. Postępuj zgodnie z instrukcjami [w te Visual Studio](remove-visual-studio.md).
2. Uruchom ponownie program inicjujący opisany w kroku 4 — usuwanie katalogu Instalator programu Visual Studio, aby [rozwiązać problemy z uaktualnieniem.](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)
3. Spróbuj zainstalować lub zaktualizować Visual Studio ponownie.

### <a name="step-7---contact-us-optional"></a>Krok 7. Kontakt z nami (opcjonalnie)

Jeśli żaden z poprzednich kroków nie pomoże Ci pomyślnie zainstalować lub [](https://visualstudio.microsoft.com/vs/support/#talktous) uaktualnić usługi Visual Studio, skontaktuj się z nami za pomocą naszej opcji pomocy technicznej czatu na żywo (tylko w języku angielskim), aby uzyskać dalszą pomoc.

## <a name="offline-installations"></a>Instalacje w trybie offline

Poniżej znajduje się tabela znanych problemów i obejścia, które mogą pomóc podczas tworzenia instalacji w trybie [offline,](create-an-offline-installation-of-visual-studio.md) a następnie instalacji z układu lokalnego.

| Problem       | Element                   | Rozwiązanie |
| ----------- | ---------------------- | -------- |
| Użytkownicy nie mają dostępu do plików. | uprawnienia (listy ACL) | Przed udostępnieniem instalacji w trybie offline upewnij się, że  zostały dostosowane uprawnienia (listy ACL), aby przyznać dostęp do odczytu innym użytkownikom. |
| Nie można zainstalować nowych obciążeń, składników lub języków.  | `--layout`  | Upewnij się, że masz dostęp do Internetu, jeśli instalujesz z częściowego układu i wybierasz obciążenia, składniki lub języki, które nie zostały wcześniej pobrane w tym częściowym układzie. |

Aby uzyskać więcej informacji na temat rozwiązywania problemów z instalacją [sieci,](create-a-network-installation-of-visual-studio.md)zobacz Rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania lub używania [programu Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Dzienniki instalacji

Dzienniki instalacji są potrzebne do rozwiązywania większości problemów z instalacją. Po przesłaniu problemu przy użyciu funkcji Zgłoś [problem](../ide/how-to-report-a-problem-with-visual-studio.md) w Instalator programu Visual Studio te dzienniki są automatycznie uwzględniane w raporcie.

Jeśli skontaktujesz się Pomoc techniczna Microsoft, może być konieczne podanie tych dzienników instalacji przy użyciu narzędzia Microsoft Visual Studio .NET Framework [Log Collection Tool.](https://www.microsoft.com/download/details.aspx?id=12493) Narzędzie do zbierania dzienników zbiera dzienniki instalacji ze wszystkich składników zainstalowanych przez program Visual Studio, w tym .NET Framework, Windows SDK i SQL Server. Zbiera również informacje o komputerze, spis Instalator Windows i informacje dziennika zdarzeń systemu Windows dotyczące Instalator programu Visual Studio, Instalator Windows i Przywracanie systemu.

Aby zebrać dzienniki:

1. [Pobierz narzędzie](https://www.microsoft.com/download/details.aspx?id=12493).
2. Otwórz administracyjny wiersz polecenia.
3. Uruchom `Collect.exe` plik z katalogu, w którym zapisano narzędzie.
4. Znajdź wynikowy `vslogs.zip` plik w `%TEMP%` katalogu, na przykład `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` .

> [!NOTE]
> Narzędzie musi być uruchamiane na tym samym koncie użytkownika, w ramach których została uruchomione instalacja, która zakończyła się niepowodzeniem. Jeśli używasz narzędzia z innego konta użytkownika, ustaw opcję , aby określić konto użytkownika, na którym została uruchomiona instalacja, która `–user:<name>` zakończyła się niepowodzeniem. Uruchom `Collect.exe -?` polecenie z wiersza polecenia administratora, aby uzyskać dodatkowe opcje i informacje o użyciu.

## <a name="live-help"></a>Pomoc na żywo

Jeśli rozwiązania wymienione w tym przewodniku rozwiązywania problemów nie pomogą Ci pomyślnie [](https://visualstudio.microsoft.com/vs/support/#talktous) zainstalować lub uaktualnić usługi Visual Studio, użyj naszej opcji pomocy technicznej dla czatów na żywo (tylko w języku angielskim), aby uzyskać dalszą pomoc.

## <a name="see-also"></a>Zobacz też

* [Napraw program Visual Studio](repair-visual-studio.md)
* [Usuń Visual Studio](remove-visual-studio.md)
* [Instalowanie i używanie Visual Studio usług platformy Azure za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
