---
title: Dzienniki kontenerów, zmienne środowiskowe & dostęp do systemu plików
description: Opisuje sposób ulepszania możliwości debugowania i diagnozowania aplikacji opartych na kontenerach w programie Visual Studio przy użyciu okna narzędzi, aby zobaczyć, co się dzieje w kontenerach, które obsługują aplikację.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 05/06/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: 3fb9a52f990a2e492c63a6e71a7cc2063110c816
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179835"
---
# <a name="how-to-view-and-diagnose-containers-in-visual-studio"></a>Jak wyświetlać i diagnozować kontenery w programie Visual Studio

Możesz zobaczyć, co się dzieje w kontenerach, które obsługują aplikację przy użyciu okna **kontenery** . Jeśli używasz wiersza polecenia do uruchamiania poleceń platformy Docker w celu wyświetlenia i zdiagnozowania, co się dzieje z kontenerami, to okno zapewnia wygodniejszy sposób monitorowania kontenerów bez opuszczania środowiska IDE programu Visual Studio.

> [!NOTE]
> Okno kontenery jest obecnie dostępne jako rozszerzenie w wersji zapoznawczej, które można [pobrać](https://aka.ms/vscontainerspreview) dla programu Visual Studio 2019.

## <a name="prerequisites"></a>Wymagania wstępne

- [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Zainstaluj [program Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
- Zainstaluj [rozszerzenie okna kontenerów](https://aka.ms/vscontainerspreview)

## <a name="view-information-about-your-containers"></a>Wyświetlanie informacji o kontenerach

Okno **kontenery** jest otwierane automatycznie po uruchomieniu kontenera projektu .NET. Aby w dowolnym momencie wyświetlić kontenery w programie Visual Studio, użyj **klawisza Ctrl**+**Q** , aby aktywować pole wyszukiwania programu Visual `Containers` Studio, a następnie wpisz i wybierz pierwszy element. Możesz również otworzyć okno **kontenery** z menu głównego. Użyj ścieżki menu **Przeglądaj** > inne**kontenery** **systemu Windows** > .  

![Zrzut ekranu karty środowisko w oknie kontenery](media/view-and-diagnose-containers/container-window.png)

Po lewej stronie zostanie wyświetlona lista kontenerów na komputerze lokalnym. Kontenery skojarzone z rozwiązaniem są wyświetlane w obszarze **kontenery rozwiązań**. Po prawej stronie zobaczysz okienko z kartami dla **środowiska**, **portów**, **dzienników**i **plików**.

> [!TIP]
> Możesz łatwo dostosować lokalizację okna narzędzia **kontenerów** w programie Visual Studio. Zobacz [Dostosowywanie układów okien w programie Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio). Domyślnie okno kontenerów jest zadokowane przy użyciu okna **czujki** , gdy debuger jest uruchomiony.

## <a name="view-environment-variables"></a>Wyświetl zmienne środowiskowe

Na karcie **środowisko** są wyświetlane zmienne środowiskowe w kontenerze. W przypadku kontenera aplikacji można ustawić te zmienne na wiele sposobów, na przykład w pliku dockerfile, w pliku. ENV lub przy użyciu opcji-e podczas uruchamiania kontenera przy użyciu polecenia Docker.

![Zrzut ekranu karty środowisko w oknie kontenery](media/view-and-diagnose-containers/container-environment-vars.png)

> [!NOTE]
> Wszelkie zmiany zmiennych środowiskowych nie są odzwierciedlone w czasie rzeczywistym. Ponadto zmienne środowiskowe na tej karcie są systemowymi zmiennymi środowiskowymi w kontenerze i nie odzwierciedlają zmiennych środowiskowych użytkownika lokalnych dla aplikacji.

## <a name="view-port-mappings"></a>Wyświetl mapowania portów

Na karcie **porty** można sprawdzić mapowania portów obowiązujące dla danego kontenera.

![Zrzut ekranu karty porty w oknie kontenery](media/view-and-diagnose-containers/container-ports.png)

Dobrze znane porty są połączone, dlatego jeśli na porcie jest dostępna zawartość, możesz kliknąć link, aby otworzyć przeglądarkę.

## <a name="view-logs"></a>Wyświetlanie dzienników

Na karcie **dzienniki** są wyświetlane wyniki `docker logs` polecenia. Domyślnie karta pokazuje strumienie stdout i stderr w kontenerze, ale można skonfigurować dane wyjściowe. Aby uzyskać szczegółowe informacje, zobacz [Rejestrowanie platformy Docker](https://docs.docker.com/config/containers/logging/).  Domyślnie karta **dzienniki** przesyła strumieniowo dzienniki, ale można je wyłączyć, wybierając przycisk **Zatrzymaj** na karcie.

![Zrzut ekranu karty Dzienniki w oknie kontenery](media/view-and-diagnose-containers/containers-logs.jpg)

Aby wyczyścić dzienniki, użyj przycisku **Wyczyść** na karcie **dzienniki** .  Aby pobrać wszystkie dzienniki, użyj przycisku **Odśwież** .

> [!NOTE]
> Program Visual Studio automatycznie przekierowuje stdout i stderr do okna **danych wyjściowych** , więc kontenery uruchomione z programu Visual Studio (czyli kontenery w sekcji **kontenery rozwiązania** ) nie będą wyświetlały dzienników na tej karcie. Zamiast tego użyj okna **danych wyjściowych** .

## <a name="view-the-filesystem"></a>Wyświetlanie systemu plików

Na karcie **pliki** można wyświetlić system plików kontenera, w tym folder aplikacji zawierający projekt.

![Zrzut ekranu karty pliki w oknie kontenerów](media/view-and-diagnose-containers/container-filesystem.png)

Aby otworzyć pliki w programie Visual Studio, przejdź do pliku, kliknij go dwukrotnie lub kliknij prawym przyciskiem myszy i wybierz polecenie **Otwórz**. Program Visual Studio otwiera pliki w trybie tylko do odczytu.

![Zrzut ekranu przedstawiający plik otwarty do wyświetlania w programie Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Za pomocą karty **pliki** można wyświetlać dzienniki aplikacji, takie jak dzienniki usług IIS, pliki konfiguracji i inne pliki zawartości w systemie plików kontenera.

## <a name="start-stop-and-remove-containers"></a>Uruchamianie, zatrzymywanie i usuwanie kontenerów

Domyślnie w oknie **kontenerów** są wyświetlane wszystkie kontenery na komputerze zarządzanym przez platformę Docker. Za pomocą przycisków paska narzędzi można uruchamiać, zatrzymywać i usuwać (usuwać) kontenerów, które nie są już potrzebne.  Ta lista jest aktualizowana dynamicznie w miarę tworzenia lub usuwania kontenerów.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o narzędziach kontenera dostępnych w programie Visual Studio, odczytując [informacje](overview.md)o narzędziach kontenerów.

## <a name="see-also"></a>Zobacz także

[Programowanie kontenerów w programie Visual Studio](/visualstudio/containers)

[Witryna Marketplace dla rozszerzeń dla programu Visual Studio](https://marketplace.visualstudio.com/)
