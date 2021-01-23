---
title: Visual Studio dla komputerów Mac narzędzia Instalatora dla aparatu Unity
description: Konfigurowanie i Instalowanie narzędzi Unity do użycia w Visual Studio dla komputerów Mac
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: f423b77f8464b05b81be2ff7cdb08a2d8b007e0d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723065"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Konfigurowanie narzędzi Visual Studio dla komputerów Mac dla aparatu Unity

W tej sekcji wyjaśniono, jak zacząć korzystać z narzędzi Visual Studio dla komputerów Mac Tools for Unity.

## <a name="install-visual-studio-for-mac"></a>Instalowanie programu Visual Studio dla komputerów Mac

### <a name="unity-bundled-installation"></a>Instalacja z pakietem Unity

Począwszy od aparatu Unity 2018,1, Visual Studio dla komputerów Mac jest domyślnym zintegrowanym środowiskiem projektowym C# (IDE) dla aparatu Unity i znajduje się w Asystencie pobierania aparatu Unity, a także narzędzia instalacji centrum Unity. Pobierz aparat Unity z [Store.Unity.com](https://store.unity.com/).

Podczas instalacji upewnij się, że Visual Studio dla komputerów Mac jest zaznaczone na liście składników do zainstalowania przy użyciu aparatu Unity:

#### <a name="unity-hub"></a>Centrum Unity

![Instalacja centrum Unity](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Asystent pobierania aparatu Unity

![instalacja Asystenta pobierania aparatu Unity](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Sprawdź dostępność aktualizacji Visual Studio dla komputerów Mac

Wersja Visual Studio dla komputerów Mac dołączonego do instalacji aparatu Unity może nie być najnowsza. Zalecane jest sprawdzenie dostępności aktualizacji, aby upewnić się, że masz dostęp do najnowszych narzędzi i funkcji.

* [Aktualizowanie Visual Studio dla komputerów Mac](update.md)

### <a name="manual-installation"></a>Instalacja ręczna

Jeśli masz już 5.6.1 aparatu Unity lub nowszego, ale nie masz Visual Studio dla komputerów Mac, możesz zainstalować Visual Studio dla komputerów Mac ręcznie. Wszystkie wersje Visual Studio dla komputerów Mac są powiązane z narzędziami Visual Studio dla komputerów Mac Tools for Unity, w tym z bezpłatną wersją Community:

* Pobierz Visual Studio dla komputerów Mac z [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/).
* Visual Studio dla komputerów Mac Tools for Unity są instalowane automatycznie podczas procesu instalacji.
* Wykonaj kroki opisane w [przewodniku instalacji](./installation.md?view=vsmac-2017&preserve-view=true) , aby uzyskać dodatkową pomoc dotyczącą instalacji.

> [!NOTE]
> Narzędzia Visual Studio dla komputerów Mac dla aparatu Unity wymagają środowiska Unity w wersji 5.6.1 lub nowszej. Aby sprawdzić, czy Visual Studio Tools for Unity są włączone w używanej wersji aparatu Unity, wybierz pozycję **informacje z aparatu** Unity z menu aparatu Unity i poszukaj tekstu "Microsoft Visual Studio Tools for Unity Enabled" w lewym dolnym rogu okna dialogowego.
>
> ![Informacje o aparacie Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Upewnij się, że rozszerzenie Visual Studio dla komputerów Mac Tools for Unity jest włączone

Mimo że rozszerzenie Visual Studio dla komputerów Mac Tools for Unity powinno być domyślnie włączone, można je potwierdzić i sprawdzić numer zainstalowanej wersji:

1. Z menu programu Visual Studio wybierz pozycję **rozszerzenia..**..

   ![Wybierz rozszerzenia](media/setup-vsmac-tools-unity-image1.png)

2. Rozwiń sekcję Programowanie gier i Potwierdź wpis Visual Studio dla komputerów Mac Tools for Unity.

   ![Wyświetl wpis Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Konfigurowanie aparatu Unity do użycia z Visual Studio dla komputerów Mac

Począwszy od aparatu Unity 2018,1, program Visual Studio powinien być domyślnym zewnętrznym edytorem skryptów w aparacie Unity. Możesz to potwierdzić lub zmienić zewnętrzny edytor skryptów na Visual Studio:

1. Wybierz pozycję **Preferencje...** z menu aparatu Unity.

   ![Wybierz Preferencje](media/setup-vsmac-tools-unity-image4.png)

2. W oknie dialogowym preferencji wybierz kartę **narzędzia zewnętrzne** .

3. Z listy rozwijanej zewnętrzny edytor skryptów wybierz pozycję **Visual Studio** (jeśli jest wyświetlana), w przeciwnym razie wybierz pozycję **Przeglądaj...**.

   ![Wybierz program Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Jeśli wybrano opcję **Przeglądaj...** , przejdź do katalogu aplikacji, a następnie wybierz pozycję Visual Studio, a następnie kliknij przycisk **Otwórz**.

   ![Wybierz pozycję Otwórz](media/setup-vsmac-tools-unity-image6.png)

5. Po wybraniu programu Visual Studio na liście **zewnętrznych edytorów skryptów** Zamknij okno dialogowe preferencji, aby zakończyć proces konfiguracji.