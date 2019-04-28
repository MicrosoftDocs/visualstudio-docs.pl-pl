---
title: Instalator programu Visual Studio dla komputerów Mac Tools for Unity
description: Konfigurowanie i instalowanie narzędzi Unity tools do użytku w programie Visual Studio dla komputerów Mac
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d490b4c1268beb4a5ad55263cb186d838005f718
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988840"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Konfigurowanie programu Visual Studio dla komputerów Mac Tools for Unity

W tej sekcji wyjaśniono, jak rozpocząć korzystanie z programu Visual Studio dla komputerów Mac Tools for Unity.

## <a name="install-visual-studio-for-mac"></a>Zainstaluj program Visual Studio dla komputerów Mac

### <a name="unity-bundled-installation"></a>Unity powiązane instalacji

Począwszy od Unity 2018.1, Visual Studio for Mac jest ustawieniem domyślnym C# zintegrowane środowisko projektowe (IDE) dla aparatu Unity i są objęte Asystenta pobieranie aparatu Unity, a także narzędzie instalacji Centrum aparatu Unity. Pobierz oprogramowanie Unity z [store.unity.com](https://store.unity.com/).

Podczas instalacji upewnij się, że zaznaczono Visual Studio dla komputerów Mac, na liście składników do zainstalowania przy użyciu aparatu Unity:

#### <a name="unity-hub"></a>Centrum platformy Unity

![Instalacja Centrum aparatu Unity](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Asystent pobieranie aparatu Unity

![Instalacja Asystenta pobieranie aparatu Unity](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Wyszukaj aktualizacje programu Visual Studio dla komputerów Mac

Wersja programu Visual Studio dla komputerów Mac dołączone instalacja aparatu Unity nie może być r. Zalecane jest, aby sprawdzał dostępność aktualizacji upewnić się, że masz dostęp do najnowszych narzędzi i funkcji.

* [Aktualizowanie programu Visual Studio dla komputerów Mac](update.md)

### <a name="manual-installation"></a>Instalacja ręczna

Jeśli masz już Unity 5.6.1 lub powyżej, ale nie zainstalowano oprogramowania Visual Studio dla komputerów Mac, można ręcznie zainstalować program Visual Studio dla komputerów Mac. Wszystkie wersje programu Visual Studio dla komputerów Mac są powiązane z programem Visual Studio dla komputerów Mac Tools for Unity, w tym dla bezpłatnej edycji Community:

* Pobierz program Visual Studio dla komputerów Mac z [visualstudio.microsoft.com](https://visualstudio.microsoft.com/).
* Program Visual Studio dla komputerów Mac Tools for Unity są instalowane automatycznie podczas procesu instalacji.
* Postępuj zgodnie z instrukcjami w [Przewodnik instalacji](/visualstudio/mac/installation/?view=vsmac-2017) instalacji dodatkowej pomocy.

> [!NOTE]
> Program Visual Studio dla komputerów Mac Tools for Unity wymaga aparatu Unity w wersji 5.6.1 lub nowszej. Aby sprawdzić, czy program Visual Studio Tools for Unity są włączone w wersji aparatu Unity, wybierz **o Unity** Unity menu i wyszukaj tekst "Microsoft Visual Studio Tools for Unity włączona" w lewym dolnym rogu okna dialogowego.
>
> ![Unity — informacje](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Upewnij się, czy włączono programu Visual Studio dla komputerów Mac Tools for Unity rozszerzenia

Gdy programu Visual Studio dla komputerów Mac Tools for Unity rozszerzenie powinno być włączone domyślnie, można to potwierdzić i sprawdź numer zainstalowanej wersji:

1. Wybierz z menu programu Visual Studio **rozszerzeń...** .

   ![Wybieranie rozszerzenia](media/setup-vsmac-tools-unity-image1.png)

2. Rozwiń sekcję Tworzenie gier i Potwierdź programu Visual Studio dla komputerów Mac Tools dla Unity wpisu.

   ![Wyświetl Unity wpisu](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Konfigurowanie aparatu Unity do użytku z programem Visual Studio dla komputerów Mac

Począwszy od Unity 2018.1, Visual Studio powinien być domyślnego edytora skryptu zewnętrznego na platformie Unity. Można to potwierdzić lub zmienić edytor skryptu zewnętrznego do programu Visual Studio:

1. Wybierz **Preferencje...**  menu aparatu Unity.

   ![Wybierz polecenie Preferencje](media/setup-vsmac-tools-unity-image4.png)

2. W oknie dialogowym Preferencje wybierz **zewnętrznych narzędzi** kartę.

3. Wybierz z listy rozwijanej zewnętrznego edytora skryptów, **programu Visual Studio** Jeśli ta opcja jest wyświetlana, w przeciwnym razie wybierz **Przeglądaj...** .

   ![Wybierz program Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Jeśli **Przeglądaj...**  została zaznaczona, przejdź do katalogu aplikacji i wybierz program Visual Studio, a następnie kliknij przycisk **Otwórz**.

   ![Wybierz przycisk Otwórz](media/setup-vsmac-tools-unity-image6.png)

5. Po wybraniu w programie Visual Studio **Edytor skryptów zewnętrznych** listy, zamknij okno dialogowe Preferencje, aby zakończyć proces konfiguracji.