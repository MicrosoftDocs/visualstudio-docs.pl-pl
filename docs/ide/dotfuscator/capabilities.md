---
title: Możliwości programu Dotfuscator
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, z przetworami, rozwiązania do zastępujące, ochrona przed zami, ochrona, Edycja Community, zaciemnianie, .NET, bezpłatnie, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Poznaj możliwości bezpłatnej kopii społeczności Dotfuscator zawartej w programie Visual Studio.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 019acd338ab49dd08255e3dc5d174cf2e371b71e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918407"
---
# <a name="capabilities-of-dotfuscator"></a>Możliwości programu Dotfuscator

Ta strona koncentruje się na możliwościach społeczności Dotfuscator z niektórymi odwołaniami do zaawansowanych opcji dostępnych w ramach [uaktualnień][upgrades].

Dotfuscator Community to system *po kompilacji* dla aplikacji .NET.
Dzięki niej użytkownicy programu Visual Studio mogą [zasłaniać zestawy][obfuscation] i wprowadzać [aktywne środki obronne][checks] do aplikacji bez konieczności Dotfuscator dostępu do oryginalnego kodu źródłowego.
Dotfuscator chroni aplikację na wiele sposobów, tworząc strategię ochrony warstwowej.

Społeczność Dotfuscator obsługuje szeroką gamę typów zestawów i aplikacji platformy .NET, w tym [platforma uniwersalna systemu Windows (platformy UWP)][uwp] i [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Ochrona własności intelektualnej

Projektowanie, zachowanie i implementacja aplikacji są formą własności intelektualnej (IP).
Jednak aplikacje utworzone dla platformy .NET są zasadniczo otwartymi książkami; można łatwo odtworzyć zestawy .NET, [ponieważ zawierają one metadane wysokiego poziomu i kod pośredni][assemblies].

Społeczność Dotfuscator zawiera podstawowe [zamieszanie platformy .NET][obfuscation] w formie [zmiany nazwy][renaming].
Zamieszanie kodu za pomocą Dotfuscator zmniejsza ryzyko nieautoryzowanego dostępu do kodu źródłowego za pomocą odtwarzania, ponieważ ważne informacje o nazewnictwie nie będą już publiczne.
W procesie zaciemniania przedstawiono również nakłady pracy, aby chronić swój kod przed badaniem — cenny krok w ustaleniu, że adres IP jest prawnie chroniony jako tajemnica handlowa.

Wiele [funkcji ochrony integralności aplikacji](#application-integrity-protection) Dotfuscator Community w dalszej częściej utrudnia proces tworzenia.
Na przykład niewłaściwy aktor może próbować dołączyć debuger do uruchomionego wystąpienia aplikacji w celu zrozumienia logiki programu.
Dotfuscator może wstrzyknąć [zachowanie antydebugowania][debug] do aplikacji, aby utrudnić tę funkcję.

## <a name="application-integrity-protection"></a>Ochrona integralności aplikacji

Oprócz ochrony kodu źródłowego należy również upewnić się, że aplikacja jest używana zgodnie z założeniami.
Osoby atakujące mogą próbować przejąć aplikację w celu obejścia zasad licencjonowania (czyli piractwa oprogramowania), kradzieży lub manipulowania danymi poufnymi obsługiwanymi przez aplikację lub zmiany zachowania aplikacji.

Społeczność Dotfuscator może wstrzyknąć [kod sprawdzania poprawności aplikacji][checks] do zestawów, w tym środki ochrony przed [naruszeniem][tamper], [antydebugowane][debug]i [antyodblokowane urządzenia][root] .
W przypadku wykrycia nieprawidłowego stanu aplikacji kod sprawdzania poprawności może [wywołać kod aplikacji, aby zająć się sytuacją w odpowiedni sposób][check-app].
Lub, jeśli wolisz, aby nie pisać kodu do obsługi nieprawidłowych zastosowań aplikacji, Dotfuscator może również wstrzyknąć zachowania [odpowiedzi][check-action] , bez konieczności modyfikacji kodu źródłowego.

Wiele z tych samych metod może być również używanych do wymuszania [terminów zakończenia okresu istnienia][shelflife] oprogramowania do oceny lub wersji próbnej.

## <a name="see-also"></a>Zobacz też

[Ten temat znajduje się w pełnym podręczniku użytkownika Dotfuscator Community][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
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
