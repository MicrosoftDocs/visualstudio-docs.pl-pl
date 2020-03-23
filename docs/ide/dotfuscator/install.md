---
title: Instalowanie programu Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, Preemptive, Preemptive Solutions, PreEmptive Protection, protection, community edition, zaciemnienie, .NET, wolny, Visual Studio 2017, Visual Studio 2019, Visual Studio, install
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Dowiedz się, jak zainstalować bezpłatną kopię społeczności dotfuscator zawartej w programie Visual Studio.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: bb659976126713a11594ad1b4aeb536510744c38
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596817"
---
# <a name="install-dotfuscator-community"></a>Instalowanie programu Dotfuscator Community

Dotfuscator Wspólnoty jest opcjonalnym składnikiem programu Visual Studio.
W tych instrukcjach wyjaśniono, jak go zainstalować.

> [!NOTE]
> Oprócz wersji Dotfuscator Wspólnoty dostarczane z wersjami programu Visual Studio, PreEmptive Solutions również okresowo udostępnia zaktualizowane wersje w swojej witrynie sieci Web.
> Jeśli chcesz pobrać **najnowszą wersję** bezpośrednio zamiast instalować z programu Visual Studio, **[kliknij tutaj, aby przejść do strony Pliki do pobrania dotfuscator][download]**.

## <a name="within-visual-studio"></a>W programie Visual Studio

::: moniker range="vs-2019"

Społeczność dotfuscator można zainstalować z ide programu Visual Studio:

1. W **polu wyszukiwania** (Ctrl+Q) wpisz . `dotfuscator` <br/> <br/> ![Pole wyszukiwania](media/install_in_vs19_12.png) <br/> <br/>

2. W wyświetlonych wynikach wyszukiwania w nagłówku *Składniki* wybierz pozycję **Zainstaluj ochronę przedwstępną - Dotfuscator**.
   * Jeśli zamiast tego widzisz, w nagłówku *Menu,* **Ochrona przedwczesna - Społeczność Dotfuscator**, a następnie Dotfuscator Wspólnoty jest już zainstalowany. Wybierz tę opcję, aby [rozpocząć][get-started].

3. Zostanie uruchomione okno Instalatora programu Visual Studio, wstępnie skonfigurowane do zainstalowania społeczności dotfuscator.
   > [!NOTE]
   > Może być konieczne podanie poświadczeń administratora, aby kontynuować.

4. W oknie Instalator programu Visual Studio kliknij pozycję *Zainstaluj*. <br/> <br/> ![Kliknięcie pozycji Zainstaluj](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Społeczność dotfuscator można zainstalować z ide programu Visual Studio:

1. Na pasku wyszukiwania **Szybkie uruchamianie** (Ctrl+Q) wpisz polecenie `dotfuscator`. <br/> <br/> ![Szybkie uruchamianie](media/install_from_vs_12.png) <br/> <br/>

2. W wyświetlonych wynikach szybkiego uruchamiania w nagłówku *Zainstaluj* wybierz pozycję **Ochrona przedwczepowa - Dotfuscator (Pojedynczy komponent).**
   * Jeśli zamiast tego widzisz, w nagłówku *Menu,* **Narzędzia - Ochrona przedwczepowa - Dotfuscator**, a następnie Dotfuscator CE jest już zainstalowany. Wybierz tę opcję, aby [rozpocząć][get-started].

3. Zostanie uruchomione okno Instalatora programu Visual Studio, wstępnie skonfigurowane do zainstalowania dotfuscatora CE.
   > [!NOTE]
   > Może być konieczne podanie poświadczeń administratora, aby kontynuować.

4. W oknie Instalator programu Visual Studio kliknij pozycję *Zainstaluj*. <br/> <br/> ![Kliknięcie pozycji Zainstaluj](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Po zakończeniu instalacji można [rozpocząć korzystanie ze społeczności Dotfuscator.][get-started]

## <a name="during-visual-studio-installation"></a>Podczas instalacji programu Visual Studio

Jeśli program Visual Studio nie został jeszcze zainstalowany, można go uzyskać w [witrynie sieci Web programu Visual Studio.][vs-install]
Po uruchomieniu zostaną wyświetlone opcje instalacji dla wybranej wersji programu Visual Studio.

::: moniker range="vs-2019"

![Opcje instalacji](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Opcje instalacji](media/install_ui_17.png)

::: moniker-end

Następnie można zainstalować Społeczność Dotfuscator jako indywidualny składnik programu Visual Studio:

1. Wybierz kartę **Poszczególne komponenty.**
2. W obszarze *Narzędzia kodu*sprawdź element *Ochrona przedwczepowa — Dotfuscator.*<br/> <br/> ![Poszczególne komponenty](media/install_individually_12.png) <br/> <br/>
3. W panelu *Podsumowanie* zostanie wyświetlona *ochrona przedwczepowa — dotfuscator* w sekcji *Poszczególne składniki.* <br/> <br/> ![Okienko Podsumowanie](media/install_individually_3.png) <br/> <br/>
4. Skonfiguruj wszelkie dalsze ustawienia instalacji odpowiednie dla danego środowiska.
5. Gdy będzie gotowy do zainstalowania programu Visual Studio, kliknij przycisk *Zainstaluj.*

Po zakończeniu instalacji można rozpocząć korzystanie ze społeczności dotfuscator. Aby uzyskać szczegółowe informacje, zobacz [stronę wprowadzenia w pełnym podręczniku użytkownika programu Dotfuscator Community][get-started].

## <a name="see-also"></a>Zobacz też

[Ten temat w pełnej Dotfuscator Community User Guide](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
