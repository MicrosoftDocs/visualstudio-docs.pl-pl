---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: System Dotfuscator zaciemniacza kodu Dotfuscator CE, system Dotfuscator Community, narzędzia PreEmptive, firmy PreEmptive Solutions PreEmptive ochrony, ochrona, wersja community edition, zasłanianie, .NET, bezpłatne, Visual Studio 2019 r, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Dowiedz się, jak możesz chronić aplikacji .NET z bezpłatną kopię programu Dotfuscator Community zawarte w Visual Studio.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bf77f2796a224d6fad81c4a1485ba82f8822cfcc
ms.sourcegitcommit: 40393347a36779230d128f2355a911632a8d458e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58866708"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***Ochrona preEmptive — Dotfuscator*** zapewnia kompleksową ochronę aplikacji .NET, łatwo mieści się w cyklu życia tworzenia bezpiecznego oprogramowania.
Użycie go do wzmacniania zabezpieczeń, ochrony i Oczyść pulpitu, telefon komórkowy, serwera i aplikacje osadzone ułatwia bezpieczne tajemnic handlowych i innych praw własności intelektualnej (IP), zmniejszyć piractwa i fałszowania oraz ochronę przed naruszeniem i nieautoryzowanego debugowania.
System Dotfuscator działa w skompilowanych zestawów bez konieczności dodatkowego programowania lub nawet dostępu do kodu źródłowego.

![Ochrona preEmptive — Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Dlaczego jest ważna ochrony

Ważne jest, aby **chronią własność intelektualną** (IP).
W kodzie aplikacji szczegółów projektu i implementacji, które mogą być uważane za adresów IP.
Jednak aplikacje tworzone w środowisku .NET Framework [zawierają istotne metadane i wysokiego poziomu kodu pośredniego][assemblies], dzięki czemu można łatwo odtworzyć, po prostu wykonując jedną z wielu bezpłatnych, automatyczne narzędzia.
Zakłócania i zatrzymywania odtwarzania możesz można zapobiec nieuprawnionym ujawnieniem adresu IP, a także pokazują, że Twój kod zawiera tajemnic handlowych.
Można Dotfuscator [zaciemniania] [ obfuscation] zestawów .NET utrudnić odtwarzania, przy zachowaniu zachować oryginalne zachowanie aplikacji.

Warto również **chronią integralność aplikacji**.
Oprócz odtwarzania nieupoważnione osoby mogą próbować pirate aplikacji, zmienić zachowanie aplikacji w czasie wykonywania lub wykonywać operacje na danych.
System Dotfuscator może wprowadzać aplikacji dzięki możliwości [wykrywanie oraz reagowanie na nieautoryzowany używa][checks], w tym naruszeniu, debugowania innych firm i urządzenia z odblokowanym dostępem.

Aby uzyskać więcej informacji na temat jak Dotfuscator dopasowuje się do cykl programowania aplikacji bezpiecznego oprogramowania, zobacz firmy PreEmptive Solutions [strony SDL App Protection][sdl-protection].

## <a name="about-dotfuscator-community"></a>About Dotfuscator Community

Twoja kopia programu Microsoft Visual Studio zawiera kopię ***PreEmptive ochrona — system Dotfuscator Community***, bezpłatne do użytku osobistego.
(To darmowa wersja była wcześniej znana jako system Dotfuscator Community Edition lub systemie Dotfuscator CE). Aby uzyskać instrukcje na temat instalowania wersji narzędzia Dotfuscator Community dołączone do programu Visual Studio, zobacz [strona instalacji][install].

System Dotfuscator Community oferuje szeroką gamę [oprogramowania ochrony i Ograniczanie funkcjonalności] [ software-protection] usług dla testerów, architektów i deweloperów.
Przykłady [zasłanianie .NET] [ obfuscation] i innych [ochrona aplikacji] [ app-protection] funkcje uwzględnione w system Dotfuscator Community są:

* *[Zmiana nazwy] [ renaming]*  identyfikatorów utrudniają odtwarzania skompilowanych zestawów.
* *[Zapobieganie odporne] [ tamper]*  do wykrywania wykonywania aplikacji zmodyfikowany i zakończyć lub odpowiadać na nie przez nikogo sesji.
* *[Zapobieganie debugowania] [ debug]*  wykrycia dołączanie debugera do uruchomionej aplikacji i zakończyć lub odpowiadać na debugowania sesji.
* *[Zapobiegających odblokowanym dostępem] [ root]*  wykryć, czy aplikacja działa na urządzenie z odblokowanym dostępem dla systemu Android i zakończyć lub odpowiadać na sesjach na tych urządzeniach.
* *[Zachowania wygaśnięcia aplikacji] [ shelflife]*  , kodowanie daty "zakończenia eksploatacji" i zakończenie sesji aplikacji wygasły.

Aby uzyskać szczegółowe informacje o tych funkcjach, w tym sposób dopasowania do strategii ochrony aplikacji, zobacz [strona możliwości][capabilities].

System Dotfuscator Community zapewnia podstawową ochronę out-of--box.
Jeszcze więcej środków ochrony aplikacji są dostępne, zarejestrowanych użytkowników programu Dotfuscator Community i użytkowników ***PreEmptive ochrona — Dotfuscator Professional***, wiodących na świecie [.NET Obfuscator] [net-obfuscator].
Aby uzyskać informacji na temat zwiększenia Dotfuscator, zobacz [stronie uaktualnienia][upgrades].

## <a name="getting-started"></a>Wprowadzenie

::: moniker range="vs-2019"

Aby rozpocząć korzystanie z narzędzia Dotfuscator Community w programie Visual Studio, należy wpisać `dotfuscator` do **pole wyszukiwania** (Ctrl + Q).

* Jeśli zainstalowano system Dotfuscator Community **pole wyszukiwania** pokaże opcji uruchamiania narzędzia Dotfuscator Community w obszarze *menu* nagłówka. Aby uzyskać więcej informacji, zobacz [stronie wprowadzenie pełnego przewodnika użytkownika system Dotfuscator Community][get-started].
* Jeśli nie zainstalowano jeszcze programu Dotfuscator Community, **pole wyszukiwania** zamiast tego wyświetli **instalowanie ochrony PreEmptive — Dotfuscator** w obszarze *poszczególne składniki* nagłówka . Zobacz [strona instalacji] [ install] Aby uzyskać szczegółowe informacje.

::: moniker-end

::: moniker range="vs-2017"

Aby rozpocząć korzystanie z narzędzia Dotfuscator Community w programie Visual Studio, należy wpisać `dotfuscator` do **Szybkie uruchamianie** paska wyszukiwania (Ctrl + Q).

* Jeśli zainstalowano system Dotfuscator Community **Szybkie uruchamianie** wyświetlenie *Menu* opcję, aby uruchomić interfejs użytkownika narzędzia Dotfuscator Community. Aby uzyskać więcej informacji, zobacz [stronie wprowadzenie pełnego przewodnika użytkownika system Dotfuscator Community][get-started].
* Jeśli nie zainstalowano jeszcze programu Dotfuscator Community, **Szybkie uruchamianie** wyświetlenie odpowiedniego *zainstalować* opcji. Zobacz [strona instalacji] [ install] Aby uzyskać szczegółowe informacje.

::: moniker-end

Możesz też pobrać **najnowszej wersji** społeczności programu Dotfuscator od [strony pobierania narzędzia Dotfuscator na preemptive.com][download].

## <a name="full-documentation"></a>Pełną dokumentację

Na tej stronie i jego podstrony stanowią ogólne omówienie funkcji programu Dotfuscator Community, a także [instrukcje dotyczące instalowania narzędzia][install].

Zobacz [pełnego przewodnika użytkownika społeczności programu Dotfuscator na preemptive.com] [ full] szczegółowe instrukcje dotyczące, w tym [sposób rozpocząć korzystanie z interfejsu użytkownika narzędzia Dotfuscator Community][get-started].

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
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
