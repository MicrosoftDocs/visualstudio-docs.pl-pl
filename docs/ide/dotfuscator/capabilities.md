---
title: Możliwości programu Dotfuscator
ms.date: 10/10/2017
ms.devlang: dotnet
ms.topic: conceptual
keywords: Narzędzia Dotfuscator, zaciemniacza kodu Dotfuscator CE, narzędzia PreEmptive firmy PreEmptive Solutions PreEmptive ochrony, ochrona, wersja community edition, zasłanianie, .NET, bezpłatną, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Dowiedz się więcej możliwości bezpłatny system Dotfuscator Community Edition zawarte w programie Visual Studio 2017.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9182593e16be2a8e09331a49427623e5c81a9a9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925361"
---
# <a name="capabilities-of-dotfuscator"></a>Możliwości programu Dotfuscator

Na tej stronie koncentruje się na możliwości programu Dotfuscator Community Edition (Dotfuscator CE) przy użyciu pewne odwołania do opcji zaawansowanych, które są dostępne za pośrednictwem [uaktualnień][upgrades].

Jest Dotfuscator *postkompilacyjnego* systemu dla aplikacji .NET.
Przy użyciu zaciemniacza kodu Dotfuscator CE programu Visual Studio użytkownicy mogą [zaciemniania zestawy][obfuscation] i wstawiać [środki obrony active][checks] do Aplikacja — a wszystko to bez konieczności dostęp do oryginalnego kodu źródłowego narzędzia Dotfuscator.
System Dotfuscator chroni aplikację na wiele sposobów, Tworzenie strategii ochrony warstwowej.

System Dotfuscator CE obsługuje szeroki zakres .NET zestawu i aplikacji typów, w tym [Windows platformy Uniwersalnej][uwp] i [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Ochrona własności intelektualnej

Projektowania aplikacji, zachowanie i implementacja są form własności intelektualnej (IP).
Aplikacje utworzone w programie .NET Framework są jednak zasadniczo Otwieranie książki; jest bardzo proste do zestawów .NET odtwarzania, [ponieważ zawierają one metadanych wysokiego poziomu i kodu pośredniego][assemblies].

System Dotfuscator CE zawiera podstawowe [zasłanianie .NET][obfuscation] w formie [zmiana nazwy][renaming].
Polega na zaciemnianiu kodu przy użyciu narzędzia Dotfuscator zmniejsza ryzyko przed nieautoryzowanym dostępem do kodu źródłowego za pomocą odtwarzania ważne informacje dotyczące nazewnictwa już nie będą dostępne publicznie.
Zasłanianie również pokazuje nakład pracy ze strony użytkownika, aby zabezpieczyć swój kod z badania - cenne krok w ustaleniu, że adres IP jest prawnie chronione jako tajemnice handlowe.

Wiele [funkcje ochrony integralności aplikacji](#application-integrity-protection) Dotfuscator CE dalsze utrudniają odtwarzanie.
Na przykład nieuprawnione może próbować dołączyć debuger do uruchomionego wystąpienia aplikacji w taki sposób, aby zrozumieć logiki programu.
System Dotfuscator może wprowadzać [zachowanie zapobieganie debugowania][debug] do aplikacji, aby to utrudniać.

## <a name="application-integrity-protection"></a>Ochrona integralności aplikacji

Oprócz ochrony kodu źródłowego, jest również ważne, aby upewnić się, że Twoja aplikacja jest używana zgodnie z założeniami.
Osoby atakujące mogą próbować przejąć kontrolę nad aplikację w celu obejścia zasad licencjonowania (czyli piractwa), wykradać lub wykonywać operacje na danych poufnych, obsługiwane przez aplikację lub zmienić sposób działania aplikacji.

System Dotfuscator CE może wprowadzać [kod sprawdzania poprawności aplikacji][checks] do zestawów, w tym [zapobieganie odporne][tamper], [ zapobieganie debugowania][debug], i [zapobiegających odblokowanym dostępem][root] miary.
Po wykryciu stanu aplikacji nieprawidłowy kod sprawdzania poprawności można [zapraszać kod aplikacji, adres do sytuacji, w odpowiedni sposób][check-app].
Lub, jeśli nie chcesz napisać kod, aby nieprawidłowe dojście korzysta z aplikacji, system Dotfuscator może również wprowadzać [odpowiedzi][check-action] zachowań, bez żadnych modyfikacji kodu źródłowego.

Wiele z tych samych metod może również Wymuszanie [terminy wycofanych z eksploatacji][shelflife] oceny lub wersja próbna oprogramowania.

## <a name="see-also"></a>Zobacz też

[W tym temacie w pełnego przewodnika użytkownika programu Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
