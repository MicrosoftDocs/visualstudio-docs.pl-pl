---
title: Możliwości programu Dotfuscator
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Społeczność dotfuscator, Dotfuscator CE, Rozwiązania wyprzedzające, Preemptive Protection, ochrona, edycja społecznościowa, zaciemnianie, .NET, bezpłatny, Visual Studio 2017, Visual Studio 2019, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Poznaj możliwości bezpłatnej kopii społeczności dotfuscator zawartej w programie Visual Studio.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 019acd338ab49dd08255e3dc5d174cf2e371b71e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75918407"
---
# <a name="capabilities-of-dotfuscator"></a>Możliwości programu Dotfuscator

Ta strona koncentruje się na możliwościach Społeczności Dotfuscator z kilkoma odniesieniami do zaawansowanych opcji dostępnych za pośrednictwem [uaktualnień.][upgrades]

Dotfuscator Community to system *po kompilacji* dla aplikacji .NET.
Dzięki niemu użytkownicy programu Visual Studio są w stanie [zaciemnić zestawy][obfuscation] i wstrzyknąć [aktywnych środków obronnych][checks] do aplikacji — wszystko bez Dotfuscator konieczności dostępu do oryginalnego kodu źródłowego.
Dotfuscator chroni aplikację na wiele sposobów, tworząc strategię ochrony warstwowej.

Dotfuscator Community obsługuje szeroką gamę typów zespołów i aplikacji .NET, w tym [universal windows platform (UWP)][uwp] i [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Ochrona własności intelektualnej

Projekt, zachowanie i implementacja aplikacji są formami własności intelektualnej (IP).
Jednak aplikacje utworzone dla platformy .NET są zasadniczo otwarte książki; można łatwo odtworzyć zestawy .NET, [ponieważ zawierają metadane wysokiego poziomu i kod pośredni.][assemblies]

Dotfuscator Wspólnoty obejmuje podstawowe [.NET zaciemnienie][obfuscation] w formie [zmiany nazwy][renaming].
Zaciemnianie kodu za pomocą dotfuscator zmniejsza ryzyko nieautoryzowanego dostępu do kodu źródłowego za pomocą inżynierii odwrotnej, ponieważ ważne informacje o nazewnictwie nie będą już publiczne.
Zaciemnienie pokazuje również wysiłek z Twojej strony, aby chronić kod przed badaniem - cenny krok w ustaleniu, że Twój adres IP jest prawnie chroniony jako tajemnica handlowa.

Wiele [funkcji ochrony integralności aplikacji](#application-integrity-protection) Dotfuscator Wspólnoty dodatkowo utrudnia inżynierię odwrotną.
Na przykład zły aktor może próbować dołączyć debugera do uruchomionego wystąpienia aplikacji w celu zrozumienia logiki programu.
Dotfuscator można wstrzyknąć [zachowanie anty-debugowania][debug] do aplikacji, aby to zablokować.

## <a name="application-integrity-protection"></a>Ochrona integralności aplikacji

Oprócz ochrony kodu źródłowego, jest również ważne, aby upewnić się, że aplikacja jest używana zgodnie z projektem.
Osoby atakujące mogą próbować przejąć kontrolę nad aplikacją w celu obejścia zasad licencjonowania (czyli piractwa komputerowego), kradzieży lub manipulowania poufnymi danymi obsługiwanymi przez aplikację lub zmiany zachowania aplikacji.

Dotfuscator Wspólnoty można wstrzyknąć [kod walidacji aplikacji][checks] do zestawów, w tym [anty-sabotażu,][tamper] [anty-debug][debug], i [anty-zakorzenione][root] środki urządzenia.
Po wykryciu nieprawidłowego stanu aplikacji kod sprawdzania poprawności może [wywołać kod aplikacji, aby rozwiązać sytuację w odpowiedni sposób.][check-app]
Lub, jeśli wolisz nie pisać kodu do obsługi nieprawidłowych zastosowań aplikacji, Dotfuscator można również wstrzyknąć zachowania [odpowiedzi,][check-action] bez konieczności modyfikowania kodu źródłowego.

Wiele z tych samych metod może być również używanych do egzekwowania [terminów zakończenia okresu próbnego][shelflife] lub oprogramowania próbnego.

## <a name="see-also"></a>Zobacz też

[Ten temat w pełnej Dotfuscator Community User Guide][full]

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
