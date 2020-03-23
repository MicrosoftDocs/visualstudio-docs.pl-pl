---
title: Uaktualnianie programu Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, Preemptive, Preemptive Solutions, PreEmptive Protection, protection, community edition, zaciemnienie, .NET, wolny, Visual Studio 2019, Visual Studio 2017, Visual Studio, uaktualnienie, wiersz polecenia
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Dowiedz się, jak uaktualnić bezpłatną kopię społeczności dotfuscator zawartej w programie Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 08492340022f772beadca8061a216de69fafc8af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596804"
---
# <a name="upgrade-dotfuscator-community"></a>Uaktualnianie programu Dotfuscator Community

Dotfuscator Wspólnoty oferuje wiele funkcji ochrony aplikacji i hartowania natychmiast do wszystkich deweloperów korzystających z programu Microsoft Visual Studio.
Jednakże, istnieje więcej funkcji dostępnych dla użytkowników, którzy uaktualnić swoją wersję Dotfuscator.

## <a name="registering-dotfuscator-community"></a>Rejestracja Społeczności Dotfuscator

Zarejestrowani użytkownicy Społeczności Dotfuscator uzyskują dostęp do dodatkowych funkcji, takich jak [obsługa wiersza polecenia,][cli]co ułatwia integrację społeczności Dotfuscator z procesem automatycznego budowania. Rejestracja zapewnia również dostęp do wbudowanego narzędzia używanego do [dekodowania zaciemnionych śladów stosu.][decode-obfuscated]

Rejestracja jest szybka, prosta i bezpłatna.
Aby zarejestrować społeczność dotfuscator, zapoznaj [się z instrukcjami zawartymi w pełnym podręczniku użytkownika społeczności Dotfuscator][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Profesjonalny

Podczas gdy Dotfuscator Community zapewnia podstawowy poziom ochrony, ***ochrona wyprzedzająca - Dotfuscator Professional*** obejmuje ulepszone transformacje zaciemniania i możliwości ochrony, takie jak:

* *Ochrona własności intelektualnej*
  * Dodatkowe opcje zmiany nazwy, w tym ulepszona indukcja przeciążenia™ i losowy wybór identyfikatora.
  * Dostęp do przekształceń zaciemniania na poziomie przedsiębiorstwa, w tym [przekształceń ukierunkowanych na pokonanie automatycznej dekompilacji kodu.][control-flow]
  * Możliwość [zasłaniania poufnych ciągów,][string-encryption]co uniemożliwia proste wyszukiwanie dekompilowanego kodu.
  * Możliwość [dyskretnego osadzania ciągów własności i dystrybucji w zestawach,][watermarking]co pozwala określić źródło nieautoryzowanych wycieków oprogramowania.
  * Możliwość [łączenia wielu zestawów w jeden][linking], co jeszcze trudniejsze dla atakujących do określenia ról elementów kodu, jak separacja problemów została wyeliminowana.
  * Możliwość [automatycznego usuwania nieużytego kodu z aplikacji][pruning], zmniejszając ilość kodu poufnego, który jest wysyłany.
* *Ochrona integralności aplikacji*
  * Dodatkowe [zachowania obrony aplikacji][check-actions].
  * Możliwość podania okresu ostrzeżenia przed upływem terminu składania wniosków.
  * Możliwość powiadamiania kodu aplikacji w okresie ostrzeżenia o zakończeniu eksploatacji lub po upływie terminu.

Dotfuscator Professional jest standardem branżowym [.NET Obfuscator][net-obfuscator] i jest odpowiedni dla deweloperów korporacyjnych wymagających ciągłego wsparcia, konserwacji i aktualizacji produktów.
Ponadto Dotfuscator Professional oferuje ściślejszą integrację z programem Visual Studio i jest licencjonowany do użytku komercyjnego.

Aby uzyskać więcej informacji na temat zaawansowanych funkcji ochrony aplikacji Dotfuscator Professional, odwiedź [stronę Dotfuscator Overview][product-about] Firmy PreEmptive Solutions i [porównaj ją ze społecznością Dotfuscator.][product-compare]
[W pełni obsługiwane wersje próbne są dostępne w preemptive.com.][eval]

## <a name="see-also"></a>Zobacz też

[Ten artykuł w pełnym Podręczniku użytkownika społeczności Dotfuscator][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html
