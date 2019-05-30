---
title: Dzienniki kontenerów, zmienne środowiskowe i dostęp do systemu plików
description: W tym artykule opisano, jak zwiększyć możliwości debugowanie i diagnozowanie aplikacji opartych na kontenerach w programie Visual Studio za pomocą okna narzędzi, aby zobaczyć, co się dzieje w kontenerach hostujących aplikację.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 05/06/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: b8e8e2db3f8f6e5aa60f3fa593caf017c349dca8
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261198"
---
# <a name="how-to-view-and-diagnose-containers-in-visual-studio"></a>Jak wyświetlać i diagnozowanie kontenerów w programie Visual Studio

Można wyświetlić, co się dzieje wewnątrz kontenerów, które hostują aplikację za pomocą **kontenery** okna. Jeśli uruchamianie poleceń Docker za pomocą wiersza polecenia do wyświetlania i Diagnozuj, co się dzieje z kontenerów, to okno umożliwia bardziej wygodne do monitorowania kontenerów bez opuszczania środowiska IDE programu Visual Studio.

> [!NOTE]
> Okno Kontejneru jest obecnie dostępna jako rozszerzenie w wersji zapoznawczej, które możesz [Pobierz](https://aka.ms/vscontainerspreview) dla programu Visual Studio 2019 r.

## <a name="prerequisites"></a>Wymagania wstępne

- [Pulpitu platformy docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Zainstaluj [Visual Studio 2019 r.](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)
- Zainstaluj [rozszerzenia okna kontenerów](https://aka.ms/vscontainerspreview)

## <a name="view-information-about-your-containers"></a>Wyświetl informacje o Twoich kontenerów

**Kontenery** zostanie otwarte okno automatycznie podczas uruchamiania konteneryzowanych projektu .NET. Aby wyświetlić swoje kontenery w programie Visual Studio, w dowolnym momencie, użyj **Ctrl**+**Q** aktywować wyszukiwania usługi Visual Studio polu, a typ `Containers` i wybierz pierwszy element. Możesz również otworzyć **kontenery** okna w menu głównym. Użyj ścieżki menu **widoku** > **Windows inne** > **kontenery**.  

![Zrzut ekranu środowiska karty w oknie kontenerów](media/view-and-diagnose-containers/container-window.png)

Po lewej stronie zobaczysz listę kontenerów na komputerze lokalnym. Kontenery skojarzone z rozwiązaniem zostaną wyświetlone w obszarze **rozwiązanie Containers**. Po prawej stronie, zobacz okienko z kartami dla **środowiska**, **porty**, **dzienniki**, i **pliki**.

> [!TIP]
> Gdzie można łatwo dostosować **kontenery** okna narzędzi jest zadokowany w programie Visual Studio. Zobacz [dostosowywanie układów okien w programie Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio). Domyślnie **kontenery** okna jest zadokowane **Obejrzyj** okna, gdy debuger jest uruchomiony.

## <a name="view-environment-variables"></a>Wyświetlanie zmiennych środowiskowych

**Środowiska** karta zawiera zmienne środowiskowe w kontenerze. Dla aplikacji kontenera można ustawić te zmienne na wiele sposobów, na przykład w pliku Dockerfile, w pliku ENV lub przy użyciu opcji -e, podczas uruchamiania kontenera za pomocą polecenia Docker.

![Zrzut ekranu środowiska karty w oknie kontenerów](media/view-and-diagnose-containers/container-environment-vars.png)

> [!NOTE]
> Wszelkie zmiany do zmiennych środowiskowych nie są uwzględniane w czasie rzeczywistym. Ponadto zmiennych środowiskowych na tej karcie są zmienne środowiskowe w kontenerze systemu i nie odzwierciedlają zmienne środowiskowe użytkownika lokalnego do aplikacji.

## <a name="view-port-mappings"></a>Widok mapowania portów

Na **porty** karcie, można sprawdzić poprawność mapowania portów, które są stosowane dla kontenera usługi.

![Zrzut ekranu porty karty w oknie kontenerów](media/view-and-diagnose-containers/container-ports.png)

Znane porty są połączone, więc jeśli wystąpią zawartości, dostępne na porcie, możesz kliknąć link, aby otworzyć w przeglądarce.

## <a name="view-logs"></a>Wyświetlanie dzienników

**Dzienniki** karta przedstawia wyniki `docker logs` polecenia. Domyślnie karta przedstawia strumienia stdout i stderr do kontenera, ale można skonfigurować dane wyjściowe. Aby uzyskać więcej informacji, zobacz [rejestrowanie Docker](https://docs.docker.com/config/containers/logging/).  Domyślnie **dzienniki** kartę strumienie dzienników, ale możesz wyłączyć, wybierając **zatrzymać** przycisku na karcie.

![Karta Zrzut ekranu z dzienników w oknie kontenerów](media/view-and-diagnose-containers/containers-logs.jpg)

Do czyszczenia dzienników, użyj **wyczyść** znajdujący się na **dzienniki** kartę.  Aby uzyskać wszystkie dzienniki, użyj **Odśwież** przycisku.

> [!NOTE]
> Program Visual Studio automatycznie przekierowuje stdout i stderr do **dane wyjściowe** okna, dlatego kontenery uruchomione w programie Visual Studio (czyli kontenerów w **rozwiązanie Containers** sekcji) nie będą wyświetlane dzienniki na tej karcie; Użyj **dane wyjściowe** okna zamiast tego.

## <a name="view-the-filesystem"></a>Widok systemu plików

Na **pliki** karcie, można wyświetlić systemu plików kontenera, w tym folder aplikacji, który zawiera projekt.

![Karta Zrzut ekranu z plików w oknie kontenerów](media/view-and-diagnose-containers/container-filesystem.png)

Aby otworzyć pliki w programie Visual Studio, przejdź do pliku i kliknij ją dwukrotnie lub kliknij prawym przyciskiem myszy i wybierz **Otwórz**. Visual Studio otwiera pliki w trybie tylko do odczytu.

![Zrzut ekranu przedstawiający otwarty plik do wyświetlenia w programie Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Za pomocą **pliki** karty, możesz wyświetlić dzienniki aplikacji, takich jak dzienniki usług IIS, pliki konfiguracji i inne pliki zawartości w z kontenerem systemu plików.

## <a name="start-stop-and-remove-containers"></a>Uruchamianie, zatrzymywanie i usuwanie kontenerów

Domyślnie **kontenery** okno pokazuje wszystkie kontenery na maszynie, która zarządza platformy Docker. Można użyć przycisków paska narzędzi, aby uruchomić, zatrzymać lub remove (Usuń) kontenera nie są już potrzebne.  Ta lista jest aktualizowana dynamicznie, jak kontenery są tworzone lub usuwane.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o dostępnych w programie Visual Studio narzędzia kontenerów, czytając [omówienie narzędzi kontenera](overview.md).

## <a name="see-also"></a>Zobacz także

[Tworzenie kontenerów w programie Visual Studio](/visualstudio/containers)

[Marketplace rozszerzeń dla programu Visual Studio](https://marketplace.visualstudio.com/)
