---
title: Team Foundation Version Control (TFVC)
description: Łączenie z Team Foundation Server lub usługi Azure DevOps z Team Foundation Version Control (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 09/05/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 1d560e3fd383e3db19c664bf027470c8da224fd2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58857804"
---
# <a name="connecting-to-team-foundation-version-control"></a>Nawiązywanie połączenia z Team Foundation Version Control

> [!NOTE]
> Team Foundation Version Control obsługi jest obecnie w wersji zapoznawczej, a niektóre funkcje nie jeszcze w pełni działa. Chętnie poznamy opinii od Ciebie na wszelkie problemy w [społeczności deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html). Zmiany są nadal pochodzić!

Repozytoriów platformy Azure oferuje dwa modele kontroli wersji: Repozytorium Git jest rozłożona Kontrola wersji i Team Foundation Version kontroli (TFVC), czyli scentralizowany formant wersji. Ten artykuł zawiera omówienie oraz punkt początkowy dla zastosowaniem funkcji TFVC za pomocą programu Visual Studio dla komputerów Mac.

## <a name="requirements"></a>Wymagania

* Visual Studio Community, Professional lub Enterprise dla komputerów Mac w wersji 7.5 lub nowszej.
* Usługom DevOps platformy Azure lub programu Team Foundation Server 2013 lub nowszym.
* Projekt w usługom DevOps platformy Azure lub Team Foundation Server skonfigurowany do używania kontroli wersji serwera Team Foundation.

## <a name="installation"></a>Instalacja

W programie Visual Studio dla komputerów Mac, wybierz **programu Visual Studio > rozszerzenia** z menu. W **galerii** zaznacz **kontroli wersji > kontroli wersji Team Foundation dla TFS i usługą VSTS** i kliknij przycisk **zainstalować**:

![Menedżer rozszerzeń](media/tfvc-install.png)

Postępuj zgodnie z monitami, aby zainstalować rozszerzenie. Po zainstalowaniu, należy ponownie uruchomić środowisko IDE.

## <a name="updating-the-extension"></a>Trwa aktualizowanie rozszerzenia

Okresowo są wprowadzone aktualizacje z rozszerzeniem TFVC. Dostęp do aktualizacji, wybierz **programu Visual Studio > rozszerzenia...**  z menu i wybierzesz **aktualizacje** kartę. Zaznacz rozszerzenie na liście i naciśnij klawisz **aktualizacji** przycisku:

![Aktualizacja przedstawiający Menedżer rozszerzenia](media/tfvc-update.png)

Naciśnij klawisz **zainstalować** w następnym oknie dialogowym odinstalowanie starego pakietu i instalacja nowego.

## <a name="using-the-add-in"></a>Za pomocą dodatku

Po zainstalowaniu rozszerzenia wybierz **kontroli wersji > DevOps programu TFS/platformy Azure > Otwórz ze zdalnego repozytorium** elementu menu.

![Element menu, aby otworzyć rozszerzenia](media/tfvc-source-control-explorer-devops.png)

Wybierz usługi VSTS lub serwera Team Foundation Server, aby rozpocząć pracę, a następnie naciśnij klawisz **Kontynuuj**:

![Łączenie z serwerem](media/tfvc-choose-server-type-devops.png)

### <a name="azure-repos-authentication"></a>Uwierzytelnianie repozytoriów platformy Azure

Po wybraniu projektu, który znajduje się na repozytoriów platformy Azure, monit o podanie szczegółów konta Microsoft:

![Połącz się z repozytoriów platformy Azure](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>Uwierzytelnianie serwera TFS

Aby połączyć z TFS, wprowadź szczegóły serwera i poświadczenia konta. Wprowadź domenę do użycia uwierzytelniania NTLM, w przeciwnym razie pozostaw puste, aby użyć uwierzytelniania podstawowego. Wybierz **Dodaj serwer**:

![Zaloguj się do serwera TFS](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Wybieranie projektu

Po użytkownik został pomyślnie uwierzytelniony, można wyświetlić listę repozytoriów, które są skojarzone z kontem w **Otwórz z kontroli źródła** okno dialogowe:

![Otwórz z dialogowe kontroli źródła z projektami wyświetlane](media/tfvc-vsts-projects.png)

To okno dialogowe jest zorganizowana przy użyciu następujących węzłów:

- Usługa Azure DevOps organizacji lub kolekcji — zostaną wyświetlone wszystkie organizacje podłączone do konta Microsoft, którego zalogowano się przy użyciu.
- Projekty — w każdej organizacji lub kolekcji, może mieć wiele projektów. Projekt jest, gdzie hostowana kod źródłowy, elementy robocze i automatyczne kompilacje.

W tym momencie wyszukiwanie i filtrowanie według nazwy projektu lub organizacji.

### <a name="adding-a-new-server"></a>Dodawanie nowego serwera

Aby dodać nowy serwer do listy, naciśnij klawisze **Dodaj hosta** znajdujący się na **Otwórz z kontroli źródła** okno dialogowe:

![Wyróżnione Dodaj przycisk, aby dodać nowy serwer do listy](media/tfvc-add-new-server.png)

Wybierz dostawcę z listy, a następnie wprowadź swoje poświadczenia:

![Okno dialogowe z wyświetloną opcją dostawcy kontroli źródła](media/tfvc-add-new-creds-devops.png)

## <a name="creating-a-new-workspace"></a>Tworzenie nowego obszaru roboczego

Aby rozpocząć pracę z projektem, musisz mieć _obszaru roboczego_. Jeśli nie masz jeszcze obszaru roboczego, możesz utworzyć je z **obszaru roboczego** combobox **Otwórz z kontroli źródła** okno dialogowe:

![Utwórz nową opcję combobox obszaru roboczego](media/tfvc-create-new-workspace.png)

Ustaw nazwę i ścieżkę lokalną dla nowego obszaru roboczego i wybierz **Utwórz obszar roboczy**:

![Wprowadź nazwę i ścieżkę lokalną dla nowego obszaru roboczego](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Za pomocą Eksploratora kodu źródłowego

Po utworzeniu obszaru roboczego i mapowany do projektu, możesz rozpocząć pracę z _Eksploratora kodu źródłowego_.

Aby otworzyć Eksploratora kodu źródłowego, zaznacz **kontroli wersji > DevOps programu TFS/platformy Azure > Eksploratorze kontroli źródła** elementu menu.

Eksplorator kodu źródłowego umożliwia nawigowanie po wszystkich zamapowanych projektów, pliki i foldery. W tym obszarze można również wykonywać wszystkie akcje kontroli podstawowego źródła takie jak:

- Pobierz najnowszą wersję
- Pobieranie określonej wersji
- Ewidencjonowanie i wyewidencjonowywanie plików
- Blokowanie i odblokowywanie plików
- Dodawanie, usuwanie i Zmień nazwy plików
- Wyświetlić historię
- Porównaj zmiany.

Wiele z tych działań są dostępne za pośrednictwem kontekst akcji dla projektu:

![Akcje menu kontekstowe dla projektu](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>Zarządzanie obszarami roboczymi

Jeśli nie utworzono jeszcze obszaru roboczego, zgodnie z opisem w [tworzenia obszaru roboczego](#creating-a-new-workspace) sekcji, można zauważyć, że Eksplorator kodu źródłowego jest puste:

![Źródło pusty Eksplorator kodu](media/tfvc-setup-empty-sce.png)

Aby skonfigurować zdalne projektu za pomocą lokalnego obszaru roboczego, użyj następujących kroków:

1. Wybierz **serwera** z pola kombi.
1. Należy pamiętać, że nie ma "żadnych obszarów roboczych" i że ścieżka lokalna jest "Niezamapowany". Wybierz **niezamapowane** łącze, aby wyświetlić **Utwórz nowy obszar roboczy** okna dialogowego.
1. Podaj nazwę obszaru roboczego, a następnie kliknij przycisk **Dodaj Folder pracy** do mapowania projektu do folderu lokalnego na komputerze:

    ![Utwórz nowe okno dialogowe obszaru roboczego przedstawiający opcje domyślne](media/tfvc-workspace1.png)

1. Wybierz folder "$", aby mapować wszystkie projekty na serwerze do tego samego obszaru roboczego, lub wybierz pojedynczego projektu, a następnie kliknij przycisk **OK**:

    ![Przeglądaj w poszukiwaniu folderu okno dialogowe wyświetloną wszystkie projekty](media/tfvc-workspace2.png)

1. Wybierz lokalizację na lokalnym komputerze, którą chcesz zamapować te projekty do, a następnie kliknij przycisk **wybierz Folder**.
1. Potwierdź szczegóły nowego obszaru roboczego, naciskając klawisz **OK**

    ![Tworzenie okna dialogowego Nowy obszar roboczy za pomocą folderu roboczego dodano](media/tfvc-workspace3.png)

Po skonfigurowaniu obszaru roboczego może można zmienić ani usunąć, klikając **zarządzanie obszarami roboczymi** przycisku w Eksploratorze kodu źródłowego.

![Zarządzanie obszarami roboczymi](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="problems-using-basic-authentication"></a>Problemów przy użyciu uwierzytelniania podstawowego

Następujące opcje może służyć do uwierzytelniania z serwerem:

- OAuth
- Podstawowy
- Ntlm

Do korzystania z uwierzytelniania podstawowego jest niezbędne do włączenia **uwierzytelniania alternatywnych poświadczeń** w usługom DevOps platformy Azure, wykonując poniższe kroki:

1. Zaloguj się do Twojej organizacji DevOps platformy Azure jako właściciel (https://dev.azure.com/{organization}/{project}).

2. Z organizacji paska narzędzi, wybierz ikonę koła zębatego, a następnie wybierz pozycję **zasad**:

    ![Wybrana opcja ustawień zasad](media/tfvc-auth2.png)

3. Sprawdź ustawienia połączenia aplikacji. Zmień te ustawienia, w oparciu o zasady zabezpieczeń:

    ![Wybrana opcja ustawień zasad](media/tfvc-auth.png)

### <a name="i-do-not-see-anything-in-tfvc"></a>Nie znajdziesz już niczego w TFVC

Aby ustawić się kontroli wersji Team Foundation (TFVC) na komputerze deweloperskim, możesz **musi** Utwórz obszar roboczy, zgodnie z opisem w [zarządzanie obszarami roboczymi](#managing-workspaces) sekcji.

W Eksploratorze kontroli źródła, naciśnij klawisz **zarządzanie obszarami roboczymi** przycisku. Wykonaj kroki do mapowania projektu do folderu na komputerze deweloperskim.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Nie widzę żadnych / all moich projektów

Po uwierzytelnieniu powinien zostać wyświetlony listy projektów. Domyślnie są wyświetlane tylko w projektach programu TFS. Aby wyświetlić innych typów projektów, zaznacz pole "Zobacz wszystkich projektów".

Należy pamiętać, że projekty, które znajdują się na serwerze nie będą widoczne, jeśli nie masz poprawne uprawnienia.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Pojawia się błąd "nie można utworzyć obszaru roboczego. Spróbuj ponownie"

Podczas próby [Utwórz nowy obszar roboczy](#creating-a-new-workspace), należy się upewnić, są spełnione następujące warunki:

- Zakaz używania nieprawidłowe znaki w nazwie obszaru roboczego.
- Nazwa musi być krótsza niż 64 znaki.
- Nie można użyć ścieżki lokalnej przez innych obszarów roboczych.

## <a name="see-also"></a>Zobacz także

- [Tworzenie i udostępnianie kodu w TFVC przy użyciu programu Visual Studio (na Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)