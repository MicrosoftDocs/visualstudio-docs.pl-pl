---
title: Dzienniki kontenerów platformy Docker, zmienne środowiskowe i dostęp do systemu plików
description: W tym artykule opisano, jak poprawić możliwość debugowania i diagnozowania aplikacji opartych na kontenerach w programie Visual Studio przy użyciu okna narzędzia, aby zobaczyć, co dzieje się wewnątrz kontenerów, które hostują aplikację.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: b4670c003c06f8d16979589a4dce5abf33d5e27d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027308"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Jak wyświetlać i diagnozować kontenery i obrazy w programie Visual Studio

Można wyświetlić, co dzieje się wewnątrz kontenerów, które hostuje aplikację przy użyciu **kontenerów** okna. Jeśli używasz do korzystania z wiersza polecenia do uruchamiania poleceń platformy Docker do wyświetlania i diagnozowania, co się dzieje z kontenerów, to okno zapewnia bardziej wygodny sposób monitorowania kontenerów bez opuszczania środowiska IDE programu Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

- [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Program Visual Studio 2019 w wersji 16.4 Wersja zapoznawcza 2](https://visualstudio.microsoft.com/downloads) lub nowsza lub jeśli używasz wcześniejszej wersji programu Visual Studio 2019, zainstaluj [rozszerzenie okna Kontenery](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Wyświetlanie informacji o kontenerach

**Okno Kontenery** otwiera się automatycznie po uruchomieniu konteneryzowanego projektu .NET. Aby wyświetlić kontenery w programie Visual Studio w dowolnym momencie, użyj `Containers` **Ctrl**+**Q,** aby uaktywnić pole wyszukiwania programu Visual Studio i wpisz i wybierz pierwszy element. Okno **Kontenery** można również otworzyć z menu głównego. Użyj ścieżki menu **Wyświetl** > inne**kontenery****systemu Windows** > .  

![Zrzut ekranu przedstawiający kartę Środowisko w oknie Kontenery](media/view-and-diagnose-containers/container-window.png)

Po lewej stronie znajduje się lista kontenerów na komputerze lokalnym. Kontenery skojarzone z rozwiązaniem są wyświetlane w obszarze **Kontenery rozwiązań.** Po prawej stronie jest widoczne okienko z kartami **dla środowiska,** **portów,** **dzienników**i **plików**.

> [!TIP]
> Można łatwo dostosować, gdzie **kontenery** okno narzędzia jest zadokowany w programie Visual Studio. Zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Domyślnie **kontenery** okna jest zadokowany z **watch** okna, gdy debuger jest uruchomiony.

## <a name="view-environment-variables"></a>Wyświetlanie zmiennych środowiskowych

Na karcie **Środowisko** są wyświetlane zmienne środowiskowe w kontenerze. W kontenerze aplikacji można ustawić te zmienne na wiele sposobów, na przykład w pliku Dockerfile, w pliku env lub przy użyciu opcji -e podczas uruchamiania kontenera przy użyciu polecenia Platformy Docker.

![Zrzut ekranu przedstawiający kartę Środowisko w oknie Kontenery](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Wszelkie zmiany zmiennych środowiskowych nie są odzwierciedlane w czasie rzeczywistym. Ponadto zmienne środowiskowe w tej karcie są zmiennymi środowiska systemowego w kontenerze i nie odzwierciedlają zmiennych środowiskowych użytkownika lokalnych do aplikacji.

## <a name="view-port-mappings"></a>Wyświetlanie mapowań portów

Na karcie **Porty** można sprawdzić mapowania portów, które obowiązują dla kontenera.

![Zrzut ekranu przedstawiający kartę Porty w oknie Kontenery](media/view-and-diagnose-containers/containers-ports.png)

Dobrze znane porty są połączone, więc jeśli na porcie jest dostępna zawartość, możesz kliknąć łącze, aby otworzyć przeglądarkę.

## <a name="view-logs"></a>Wyświetlanie dzienników

Na karcie **Dzienniki** są `docker logs` wyświetlane wyniki polecenia. Domyślnie karta pokazuje strumienie stdout i stderr na kontenerze, ale można skonfigurować dane wyjściowe. Aby uzyskać szczegółowe informacje, zobacz [Rejestrowanie platformy Docker](https://docs.docker.com/config/containers/logging/).  Domyślnie karta **Dzienniki** strumieni dzienników, ale można wyłączyć, że wybierając **przycisk Zatrzymaj** na karcie.

![Zrzut ekranu przedstawiający kartę Dzienniki w oknie Kontenery](media/view-and-diagnose-containers/containers-logs.png)

Aby wyczyścić dzienniki, użyj przycisku **Wyczyść** na karcie **Dzienniki.**  Aby uzyskać wszystkie dzienniki, użyj przycisku **Odśwież.**

> [!NOTE]
> Visual Studio automatycznie przekierowuje stdout i stderr do okna **dane wyjściowe** po uruchomieniu bez debugowania z kontenerami systemu Windows, więc kontenery systemu Windows uruchomione z programu Visual Studio przy użyciu **ctrl**+**F5** nie będą wyświetlać dzienników na tej karcie; zamiast tego użyj okna **Dane wyjściowe.**

## <a name="view-the-filesystem"></a>Wyświetlanie systemu plików

Na karcie **Pliki** można wyświetlić system plików kontenera, w tym folder aplikacji zawierający projekt.

![Zrzut ekranu przedstawiający kartę Pliki w oknie Kontenery](media/view-and-diagnose-containers/container-filesystem.png)

Aby otworzyć pliki w programie Visual Studio, przejdź do pliku i kliknij go dwukrotnie lub kliknij go prawym przyciskiem myszy i wybierz polecenie **Otwórz**. Program Visual Studio otwiera pliki w trybie tylko do odczytu.

![Zrzut ekranu przedstawiający plik otwarty do wyświetlenia w programie Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Za pomocą karty **Pliki** można wyświetlać dzienniki aplikacji, takie jak dzienniki usług IIS, pliki konfiguracyjne i inne pliki zawartości w systemie plików kontenera.

## <a name="start-stop-and-remove-containers"></a>Uruchamianie, zatrzymywania i usuwania pojemników

Domyślnie **kontenery** okno pokazuje wszystkie kontenery na komputerze, który zarządza docker. Za pomocą przycisków paska narzędzi można uruchamiać, zatrzymywać lub usuwać (usuwać) kontener, który nie jest już potrzebny.  Ta lista jest dynamicznie aktualizowana, gdy kontenery są tworzone lub usuwane.

## <a name="open-a-terminal-window-in-a-running-container"></a>Otwieranie okna terminala w uruchomionym kontenerze

Okno terminala (wiersz polecenia lub powłoka interaktywna) można otworzyć w kontenerze za pomocą przycisku **Otwórz okno terminala** w oknie **Kontener.**

![Zrzut ekranu przedstawiający okno otwierania terminala w oknie Kontenery](media/view-and-diagnose-containers/containers-open-terminal-window.png)

W przypadku kontenerów systemu Windows zostanie otwarty wiersz polecenia systemu Windows. W przypadku kontenerów systemu Linux otwiera okno przy użyciu powłoki bash.

![Zrzut ekranu przedstawiający okno bash](media/view-and-diagnose-containers/container-bash-window.png)

Zwykle okno terminalu otwiera się poza programem Visual Studio jako oddzielne okno. Jeśli chcesz, aby środowisko wiersza polecenia zintegrowane z visual studio IDE jako okno narzędzia dokowania, można zainstalować [Whack Whack Terminal](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Dołączanie debugera do procesu

Debugera można dołączyć do procesu, który jest uruchomiony w kontenerze za pomocą przycisku **Dołącz do procesu** na pasku narzędzi okna Kontenery. Korzystając z tego przycisku, pojawi się okno dialogowe **Dołącz do procesu** i pokazuje dostępne procesy uruchomione w kontenerze.  

![Zrzut ekranu przedstawiający okno dialogowe Dołączanie do procesu](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Można dołączyć do procesów zarządzanych w kontenerze. Aby wyszukać proces w innym kontenerze, użyj przycisku **Znajdź** i wybierz inny kontener w oknie dialogowym **Wybierz kontener platformy Docker.**

## <a name="viewing-images"></a>Wyświetlanie obrazów

Obrazy można również wyświetlać na komputerze lokalnym za pomocą karty **Obrazy** w oknie **Kontenery.** Obrazy pobrane z zewnętrznych repozytoriów są zgrupowane razem w widoku drzewa. Wybierz obraz, aby sprawdzić szczegóły obrazu.

Aby usunąć obraz, kliknij prawym przyciskiem myszy obraz w widoku drzewa i wybierz polecenie **Usuń**lub zaznacz obraz, a następnie użyj przycisku **Usuń** na pasku narzędzi.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o narzędziach kontenerów dostępnych w programie Visual Studio, czytając [omówienie narzędzi kontenerów](overview.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie kontenerów w programie Visual Studio](/visualstudio/containers)

[Marketplace rozszerzeń dla programu Visual Studio](https://marketplace.visualstudio.com/)
