---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: overview
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, PreEmptive, PreEmptive Solutions, PreEmptive Protection, ochrona, community edition, zaciemnianie, .NET, bezpłatne, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Dowiedz się, jak chronić aplikacje platformy .NET za pomocą bezpłatnej kopii programu Dotfuscator Community zawartej w programie Visual Studio.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 7a8602dc99ba63e6cba5035636af0fbd47263e58
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769491"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

Program ***PreEmptive Protection — Dotfuscator*** zapewnia kompleksową ochronę aplikacji platformy .NET, którą można łatwo dopasować do cyklu życia tworzenia bezpiecznego oprogramowania.
Umożliwia on wzmacnianie zabezpieczeń, ochronę oraz oczyszczanie aplikacji klasycznych, mobilnych, serwerowych i osadzonych, co pozwala chronić tajemnice handlowe i inną własność intelektualną, ograniczać piractwo i fałszowanie oraz zapewniać ochronę przed manipulacjami i nieautoryzowanym debugowaniem.
Program Dotfuscator działa ze skompilowanymi zestawami bez konieczności dodatkowego programowania, a nawet uzyskiwania dostępu do kodu źródłowego.

![PreEmptive Protection — Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Dlaczego ochrona jest ważna

**Ochrona własności intelektualnej** jest ważną kwestią.
Kod aplikacji zawiera szczegółowe informacje o projekcie i implementacji, które można uznać za własność intelektualną.
Jednak aplikacje opracowywane na platformie .NET Framework [zawierają istotne metadane i kod pośredni wysokiego poziomu][assemblies], co pozwala łatwo je odtwarzać — wystarczy użyć jednego z wielu bezpłatnych, zautomatyzowanych narzędzi.
Zakłócając i blokując odtwarzanie, można zapobiec nieautoryzowanemu ujawnianiu własności intelektualnej, a także wskazać, że kod zawiera tajemnice handlowe.
Program Dotfuscator może [zaciemniać][obfuscation] zestawy platformy .NET, aby utrudnić odtwarzanie, zachowując przy tym oryginalne działanie aplikacji.

Ważna jest też **ochrona integralności aplikacji**.
Oprócz odtwarzania, osoby atakujące mogą próbować tworzyć pirackie wersje aplikacji, zmieniać jej zachowanie w czasie wykonywania lub manipulować danymi.
Program Dotfuscator może dodać do aplikacji możliwość [wykrywania nieautoryzowanych zastosowań i reagowania na nie][checks], co obejmuje manipulowanie, debugowanie przez osoby trzecie oraz odblokowywanie dostępu do urządzeń.

Aby uzyskać więcej informacji o tym, jakie jest miejsce programu Dotfuscator w cyklu tworzenia bezpiecznego oprogramowania, zobacz [stronę firmy PreEmptive Solutions dotyczącą ochrony aplikacji w cyklu tworzenia oprogramowania][sdl-protection].

## <a name="about-dotfuscator-community"></a>Informacje o programie Dotfuscator Community

Twoja kopia programu Microsoft Visual Studio zawiera kopię ***programu PreEmptive Protection — Dotfuscator Community*** do bezpłatnego użytku osobistego.
(Ta bezpłatna wersja była wcześniej nazywana Dotfuscator Community Edition lub Dotfuscator CE). Aby uzyskać instrukcje dotyczące sposobu instalowania programu Dotfuscator Community dołączonego do programu Visual Studio, zobacz [stronę instalacji][install].

Program Dotfuscator Community oferuje szereg usług [ochrony oprogramowania i wzmacniania zabezpieczeń][software-protection] dla deweloperów, architektów i testerów.
Oto przykłady funkcji [zaciemniania na platformie .NET][obfuscation] i innych funkcji [ochrony aplikacji][app-protection] za pomocą programu Dotfuscator Community:

* *[Zmienianie nazw][renaming]* identyfikatorów w celu utrudnienia odtwarzania skompilowanych zestawów.
* *[Ochrona przed manipulacją][tamper]* w celu wykrywania naruszonych aplikacji oraz kończenia naruszonych sesji lub reagowania na nie.
* *[Ochrona przed debugowaniem][debug]* w celu wykrywania dołączania debugera do uruchomionej aplikacji oraz kończenia debugowanych sesji lub reagowania na nie.
* *[Ochrona przed odblokowywaniem dostępu do urządzeń][root]* w celu wykrywania, czy aplikacja jest uruchomiona na urządzeniu z systemem Android z odblokowanym dostępem, oraz kończenia sesji na takich urządzeniach lub reagowania na nie.
* *[Funkcje wygasania aplikacji][shelflife]* , które pozwalają kodować datę zakończenia użytkowania oraz kończyć wygasłe sesje aplikacji.

Aby uzyskać szczegółowe informacje o tych funkcjach, włącznie z ich miejscem w strategii ochrony aplikacji, zobacz [stronę dotyczącą możliwości][capabilities].

Program Dotfuscator Community zawiera podstawowe funkcje ochrony gotowe do użycia.
Jeszcze więcej metod ochrony aplikacji jest dostępnych dla zarejestrowanych użytkowników programu Dotfuscator Community oraz dla użytkowników programu ***PreEmptive Protection — Dotfuscator Professional***, który jest wiodącym na świecie [narzędziem do zaciemniania dla platformy .NET][net-obfuscator].
Aby uzyskać informacje o rozszerzaniu programu Dotfuscator, zobacz [stronę dotyczącą uaktualnień][upgrades].

## <a name="getting-started"></a>Wprowadzenie

::: moniker range="vs-2019"

Aby zacząć używać programu Dotfuscator Community z poziomu programu Visual Studio, wpisz `dotfuscator` w **polu wyszukiwania** (Ctrl+Q).

* Jeśli program Dotfuscator Community jest już zainstalowany, w **polu wyszukiwania** pojawi się opcja uruchomienia programu Dotfuscator Community w obszarze nagłówka *Menu*. Aby uzyskać szczegółowe informacje, zobacz [stronę wprowadzenia w pełnym podręczniku użytkownika programu Dotfuscator Community][get-started].
* Jeśli program Dotfuscator Community nie jest jeszcze zainstalowany, w **polu wyszukiwania** pojawi się pozycja **Zainstaluj program PreEmptive Protection — Dotfuscator** w obszarze nagłówka *Pojedyncze składniki*. Aby uzyskać szczegółowe informacje, zobacz [stronę dotyczącą instalacji][install].

::: moniker-end

::: moniker range="vs-2017"

Aby zacząć używać programu Dotfuscator Community z poziomu programu Visual Studio, wpisz `dotfuscator` na pasku wyszukiwania **Szybkie uruchamianie** (Ctrl+Q).

* Jeśli program Dotfuscator Community jest już zainstalowany, na pasku **Szybkie uruchamianie** pojawi się opcja *Menu* umożliwiająca uruchomienie interfejsu użytkownika programu Dotfuscator Community. Aby uzyskać szczegółowe informacje, zobacz [stronę wprowadzenia w pełnym podręczniku użytkownika programu Dotfuscator Community][get-started].
* Jeśli program Dotfuscator Community nie jest jeszcze zainstalowany, na pasku **Szybkie uruchamianie** pojawi się odpowiednia opcja *Zainstaluj*. Aby uzyskać szczegółowe informacje, zobacz [stronę dotyczącą instalacji][install].

::: moniker-end

Możesz też uzyskać **najnowszą wersję** programu Dotfuscator Community ze [strony plików programu Dotfuscator do pobrania w witrynie preemptive.com][download].

## <a name="full-documentation"></a>Pełna dokumentacja

Ta strona i jej podstrony zawierają ogólne omówienie funkcji programu Dotfuscator Community, a także [instrukcje dotyczące instalowania tego narzędzia][install].

Zobacz [pełny podręcznik użytkownika programu Dotfuscator w witrynie preemptive.com][full], aby uzyskać szczegółowe instrukcje dotyczące użytkowania, obejmujące [rozpoczynanie korzystania z interfejsu użytkownika programu Dotfuscator Community][get-started].

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
