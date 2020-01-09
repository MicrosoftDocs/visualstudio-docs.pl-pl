---
title: Instalowanie programu Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, zastępujące rozwiązania, ochrona przed ponowną ochroną, ochrona, Edycja, wersja społecznościowa, mieszanie, .NET, bezpłatnie, Visual Studio 2017, Visual Studio 2019, Visual Studio, instalacja
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
description: Dowiedz się, jak zainstalować bezpłatną kopię społeczności Dotfuscator w programie Visual Studio.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: bb659976126713a11594ad1b4aeb536510744c38
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596817"
---
# <a name="install-dotfuscator-community"></a>Instalowanie programu Dotfuscator Community

Społeczność Dotfuscator jest opcjonalnym składnikiem programu Visual Studio.
Te instrukcje wyjaśniają, jak ją zainstalować.

> [!NOTE]
> Oprócz wersji Dotfuscator Community dostarczonych z wersjami programu Visual Studio, rozwiązania do zastępujące również okresowo udostępniają zaktualizowane wersje w witrynie sieci Web.
> Jeśli chcesz pobrać **najnowszą wersję** bezpośrednio, zamiast instalować ją z programu Visual Studio, **[kliknij tutaj, aby przejść do strony pliki do pobrania Dotfuscator][download]** .

## <a name="within-visual-studio"></a>W programie Visual Studio

::: moniker range="vs-2019"

Społeczność Dotfuscator można zainstalować z poziomu środowiska IDE programu Visual Studio:

1. W **polu wyszukiwania** (Ctrl + Q) wpisz `dotfuscator`. <br/> <br/> Pole wyszukiwania ![](media/install_in_vs19_12.png) <br/> <br/>

2. W wyświetlonych wynikach wyszukiwania w obszarze nagłówka *składniki* wybierz pozycję **Zainstaluj zastępujące ochronę — Dotfuscator**.
   * Jeśli zamiast tego zobaczysz, w nagłówku *menu* , **Dotfuscator Protection**, a następnie społeczność Dotfuscator jest już zainstalowana. Wybierz tę opcję, [Aby rozpocząć][get-started].

3. Zostanie uruchomione okno Instalator programu Visual Studio, które zostało wstępnie skonfigurowane w celu zainstalowania społeczności Dotfuscator.
   > [!NOTE]
   > Aby kontynuować, może być konieczne podanie poświadczeń administratora.

4. W oknie Instalator programu Visual Studio kliknij przycisk *Instaluj*. <br/> <br/> ![kliknij pozycję Zainstaluj](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Społeczność Dotfuscator można zainstalować z poziomu środowiska IDE programu Visual Studio:

1. Na pasku wyszukiwania **szybkiego uruchamiania** (Ctrl + Q) wpisz `dotfuscator`. <br/> <br/> ![Szybkie uruchamianie](media/install_from_vs_12.png) <br/> <br/>

2. W wyświetlonych wynikach szybkiego uruchamiania w obszarze nagłówek *instalacji* wybierz pozycję **Ochrona przed ponownymi zabezpieczeniami — Dotfuscator (poszczególne składniki)** .
   * Jeśli zamiast tego zobaczysz, w obszarze *menu* nagłówka, **Narzędzia — ochrona przed zaDotfuscator**, a następnie Dotfuscator CE jest już zainstalowany. Wybierz tę opcję, [Aby rozpocząć][get-started].

3. Zostanie uruchomione okno Instalator programu Visual Studio, które zostało wstępnie skonfigurowane w celu zainstalowania Dotfuscator CE.
   > [!NOTE]
   > Aby kontynuować, może być konieczne podanie poświadczeń administratora.

4. W oknie Instalator programu Visual Studio kliknij przycisk *Instaluj*. <br/> <br/> ![kliknij pozycję Zainstaluj](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Po zakończeniu instalacji możesz [zacząć korzystać z społeczności Dotfuscator][get-started].

## <a name="during-visual-studio-installation"></a>Podczas instalacji programu Visual Studio

Jeśli jeszcze nie zainstalowano programu Visual Studio, można uzyskać Instalatora z [witryny internetowej programu Visual Studio][vs-install].
Po uruchomieniu programu zostaną wyświetlone opcje instalacji dla wybranej wersji programu Visual Studio.

::: moniker range="vs-2019"

![Opcje instalacji](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Opcje instalacji](media/install_ui_17.png)

::: moniker-end

Następnie można zainstalować społeczność Dotfuscator jako pojedynczy składnik programu Visual Studio:

1. Wybierz kartę **poszczególne składniki** .
2. W obszarze *Narzędzia kodu*Sprawdź element *Dotfuscator Protection* .<br/> <br/> ![poszczególnych składników](media/install_individually_12.png) <br/> <br/>
3. W panelu *Podsumowanie* zostanie wyświetlona wartość *zastępują ochronę Dotfuscator* w sekcji *poszczególne składniki* . <br/> <br/> ](media/install_individually_3.png) ![okienku podsumowania <br/> <br/>
4. Skonfiguruj wszelkie dalsze ustawienia instalacji odpowiednie dla danego środowiska.
5. Gdy wszystko jest gotowe do zainstalowania programu Visual Studio, kliknij przycisk *Instaluj* .

Po zakończeniu instalacji możesz zacząć korzystać z społeczności Dotfuscator. Aby uzyskać szczegółowe informacje, zobacz [stronę wprowadzenie podręcznika użytkownika Dotfuscator][get-started].

## <a name="see-also"></a>Zobacz także

[Ten temat znajduje się w pełnym podręczniku użytkownika Dotfuscator Community](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
