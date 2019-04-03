---
title: Upgrade Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Narzędzia Dotfuscator, system Dotfuscator Community, zaciemniacza kodu Dotfuscator CE, narzędzia PreEmptive, firmy PreEmptive Solutions PreEmptive ochrony, ochrona, wersja community edition, zasłanianie, .NET, bezpłatne, Visual Studio 2019 r, Visual Studio 2017, Visual Studio, uaktualniania, wiersza polecenia
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
description: Dowiedz się, jak uaktualnić bezpłatną kopię programu Dotfuscator Community zawarte w Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cee876a3904d5c47b43b58793087c901e8444dd3
ms.sourcegitcommit: 40393347a36779230d128f2355a911632a8d458e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58866682"
---
# <a name="upgrade-dotfuscator-community"></a>Upgrade Dotfuscator Community

System Dotfuscator Community oferuje wiele ochrona aplikacji i funkcje ograniczania funkcjonalności natychmiast dla wszystkich deweloperów przy użyciu programu Microsoft Visual Studio.
Jednak istnieją więcej funkcji dostępne dla użytkowników, którzy uaktualnić swoją wersję narzędzia Dotfuscator.

## <a name="registering-dotfuscator-community"></a>Registering Dotfuscator Community

Zarejestrowani użytkownicy programu Dotfuscator Community uzyskać dostęp do dodatkowych funkcji, takich jak [obsługi wiersza polecenia][cli], który można łatwo zintegrować system Dotfuscator Community proces automatycznej kompilacji . Rejestrowanie udziela również dostępu do wbudowanych narzędziem używanym do [dekodowanie ślady stosu zaciemnionego][decode-obfuscated].

Rejestracja jest szybkie, prosty i bezpłatnie.
Aby zarejestrować system Dotfuscator Community, zobacz [instrukcje pełnego przewodnika użytkownika system Dotfuscator Community][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

System Dotfuscator Community zapewnia podstawowy poziom ochrony, jednocześnie ***PreEmptive ochrona — Dotfuscator Professional*** obejmuje ulepszone zasłanianie transformacje i funkcje ochrony, takie jak:

* *Ochrona własności intelektualnej*
  * Dodatkowe zmiany nazwy opcji obejmujących Enhanced Overload Induction™ i losowy identyfikator wyboru.
  * Dostęp do klasy korporacyjnej zasłanianie przekształceń, w tym [przekształcenia celem udaremniając zautomatyzowane dekompilacji kodu][control-flow].
  * Możliwość [zasłaniać poufnych ciągi][string-encryption], tworzenie prostego wyszukiwania kodu dekompilowanych niemożliwe.
  * Możliwość [domyślić osadzanie ciągów prawo własności i dystrybucji w zestawy][watermarking], co pozwala określić źródło nieautoryzowany przecieki oprogramowania.
  * Możliwość [połączyć wiele zestawów w jednym][linking], co jeszcze bardziej utrudnia osobom atakującym Określanie ról elementów kodu, jak został wyeliminowany separacji zagadnień.
  * Możliwość [automatycznie Usuń nieużywany kod z aplikacji][pruning], co zmniejsza ilość poufnych kod, który jest dostarczany.
* *Ochrona integralności aplikacji*
  * Dodatkowe [zachowania defense aplikacji][check-actions].
  * Możliwość zapewnienia okresie ostrzeżenia, przed upływem ostatecznego terminu wycofanych z eksploatacji aplikacji.
  * Zdolność do powiadamiania kod aplikacji, w okresie ostrzeżenia wycofanych z eksploatacji lub po upływie ostatecznego terminu.

Dotfuscator Professional jest standardem branżowym [.NET Obfuscator] [ net-obfuscator] jest odpowiednia dla deweloperów w przedsiębiorstwach wymagających bieżących aktualizacji pomocy technicznej, konserwacja i produkt.
Ponadto system Dotfuscator Professional oferuje ściślejszą integrację z programem Visual Studio i jest licencjonowany do użytku komercyjnego.

Aby uzyskać więcej informacji o funkcje ochrony aplikacji zaawansowane narzędzia Dotfuscator Professional, odwiedź stronę firmy PreEmptive Solutions [strony Przegląd programu Dotfuscator] [ product-about] i [go do porównania System Dotfuscator Community][product-compare].
[W pełni obsługiwane wersje próbne są dostępne pod adresem preemptive.com][eval].

## <a name="see-also"></a>Zobacz też

[W tym artykule w pełnego przewodnika użytkownika system Dotfuscator Community][full]

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