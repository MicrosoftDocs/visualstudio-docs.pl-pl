---
title: Konfigurowanie programu Visual Studio dla komputerów Mac Tools for Unity
description: Konfigurowanie i instalowanie narzędzi Unity do użytku w programie Visual Studio dla komputerów Mac
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d490b4c1268beb4a5ad55263cb186d838005f718
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79303282"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Konfigurowanie programu Visual Studio dla komputerów Mac Tools for Unity

W tej sekcji wyjaśniono, jak rozpocząć korzystanie z programu Visual Studio dla komputerów Mac Tools for Unity.

## <a name="install-visual-studio-for-mac"></a>Instalowanie programu Visual Studio dla komputerów Mac

### <a name="unity-bundled-installation"></a>Instalacja w pakiecie Unity

Począwszy od Unity 2018.1, Visual Studio dla komputerów Mac jest domyślnym środowiskiem programistycznym (IDE) zintegrowanym w języku C# dla unity i jest zawarte w Unity Download Assistant, a także w narzędziu instalacyjnym Unity Hub. Pobierz Unity z [store.unity.com](https://store.unity.com/).

Podczas instalacji upewnij się, że program Visual Studio dla komputerów Mac jest sprawdzany na liście składników do zainstalowania w unity:

#### <a name="unity-hub"></a>Centrum Jedności

![instalacja koncentratora unity](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Asystent pobierania Unity

![instalacja asystenta pobierania unity](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Sprawdzanie dostępności aktualizacji programu Visual Studio dla komputerów Mac

Wersja programu Visual Studio dla komputerów Mac dołączonej do instalacji Unity może nie być najnowsza. Zaleca się sprawdzanie dostępności aktualizacji, aby upewnić się, że masz dostęp do najnowszych narzędzi i funkcji.

* [Aktualizowanie programu Visual Studio dla komputerów Mac](update.md)

### <a name="manual-installation"></a>Instalacja ręczna

Jeśli masz już unity 5.6.1 lub nowszy, ale nie masz visual studio dla komputerów Mac, można zainstalować visual studio dla komputerów Mac ręcznie. Wszystkie wersje programu Visual Studio dla komputerów Mac są dołączone do programu Visual Studio for Mac Tools for Unity, w tym bezpłatnej wersji społecznościowej:

* Pobierz program Visual Studio dla komputerów Mac z [visualstudio.microsoft.com](https://visualstudio.microsoft.com/).
* Visual Studio for Mac Tools for Unity są instalowane automatycznie podczas procesu instalacji.
* Postępuj zgodnie z instrukcjami w [przewodniku instalacji,](/visualstudio/mac/installation/?view=vsmac-2017) aby uzyskać dodatkową pomoc dotyczącą instalacji.

> [!NOTE]
> Visual Studio for Mac Tools for Unity wymaga unity w wersji 5.6.1 lub nowszej. Aby sprawdzić, czy narzędzia programu Visual Studio dla unity są włączone w wersji Unity, wybierz **o jedności** z menu Unity i poszukaj tekstu "Microsoft Visual Studio Tools for Unity enabled" w lewym dolnym rogu okna dialogowego.
>
> ![Więcej o: Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Upewnij się, że jest włączone rozszerzenie Visual Studio Tools for Mac Tools for Unity

Podczas gdy rozszerzenie Visual Studio For Mac Tools for Unity powinno być domyślnie włączone, możesz to potwierdzić i sprawdzić numer zainstalowanej wersji:

1. Z menu Visual Studio wybierz polecenie **Rozszerzenia...**.

   ![Wybierz rozszerzenia](media/setup-vsmac-tools-unity-image1.png)

2. Rozwiń sekcję Tworzenie gier i potwierdź wpis Visual Studio dla komputerów Mac Tools for Unity.

   ![Wyświetl wpis jedności](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Konfigurowanie unity do użytku z programem Visual Studio dla komputerów Mac

Począwszy od Unity 2018.1, Visual Studio powinien być domyślny edytor skryptów zewnętrznych w Unity. Można to potwierdzić lub zmienić zewnętrzny edytor skryptów na Visual Studio:

1. Wybierz **preferencje...** z menu Jedność.

   ![Wybierz preferencje](media/setup-vsmac-tools-unity-image4.png)

2. W oknie dialogowym Preferencje wybierz kartę **Narzędzia zewnętrzne.**

3. Z listy rozwijanej Edytor skryptów zewnętrznych wybierz pozycję **Visual Studio,** jeśli jest na liście, w przeciwnym razie wybierz **pozycję Przeglądaj...**.

   ![Wybierz program Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Jeśli wybrano **opcję Przeglądaj...** przejdź do katalogu Aplikacje i wybierz pozycję Visual Studio, a następnie kliknij przycisk **Otwórz**.

   ![Wybierz otwórz](media/setup-vsmac-tools-unity-image6.png)

5. Po wybraniu programu Visual Studio na liście **Edytor skryptów zewnętrznych** zamknij okno dialogowe Preferencje, aby zakończyć proces konfiguracji.