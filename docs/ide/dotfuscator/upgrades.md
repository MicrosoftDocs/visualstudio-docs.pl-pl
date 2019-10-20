---
title: Uaktualnianie programu Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, zastępujące rozwiązania, ochrona przed przetworami, ochrona, Edycja, wersja Community, zaciemnianie, .NET, bezpłatnie, Visual Studio 2019, Visual Studio 2017, Visual Studio, upgrade, wiersz polecenia
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
description: Dowiedz się, jak uaktualnić bezpłatną kopię społeczności Dotfuscator w programie Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 78a26da7734e4fa74a9b312b41786caca4b7cc67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652822"
---
# <a name="upgrade-dotfuscator-community"></a>Uaktualnianie programu Dotfuscator Community

Dotfuscator Community oferuje wiele funkcji ochrony aplikacji i ograniczania funkcjonalności natychmiast do wszystkich deweloperów korzystających z Microsoft Visual Studio.
Dostępne są jednak więcej funkcji dla użytkowników, którzy uaktualniają swoją wersję Dotfuscator.

## <a name="registering-dotfuscator-community"></a>Rejestrowanie społeczności Dotfuscator

Zarejestrowani Użytkownicy Dotfuscator społeczność uzyskują dostęp do dodatkowych funkcji, takich jak [Obsługa wiersza polecenia][cli], dzięki czemu można łatwo zintegrować społeczność Dotfuscator z zautomatyzowanym procesem kompilacji. Rejestracja uprawnia również do korzystania z wbudowanego narzędzia służącego do [dekodowania śladów stosu][decode-obfuscated].

Rejestracja jest szybka, prosta i bezpłatna.
Aby zarejestrować społeczność Dotfuscator, zapoznaj się z [instrukcjami zawartymi w podręczniku użytkownika w pełni Dotfuscator][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Mimo że społeczność Dotfuscator zapewnia podstawowy poziom ochrony, ochrona przed zaawansowaną ***— Dotfuscator Professional*** obejmuje ulepszone przekształcenia zaciemniania i funkcje ochrony, takie jak:

* *Ochrona własności intelektualnej*
  * Dodatkowe opcje zmiany nazwy, w tym ulepszone™ Przeciążenie i losowe Wybieranie identyfikatora.
  * Dostęp do transformacji zaciemniania na poziomie przedsiębiorstwa, w tym [transformacji przeznaczonych do pokonania zautomatyzowanej dekompilacji kodu][control-flow].
  * Możliwość [przesłaniania poufnych ciągów][string-encryption], co sprawia, że proste wyszukiwanie nieskompilowanego kodu jest niemożliwe.
  * Możliwość [niejawnego osadzania własności i parametrów dystrybucji w zestawach][watermarking], co pozwala określić źródło przecieków nieautoryzowanego oprogramowania.
  * Możliwość [łączenia wielu zestawów w jeden][linking], co utrudnia osobom atakującym określenie ról elementów kodu, ponieważ rozdzielenie problemów zostało wyeliminowane.
  * Możliwość [automatycznego usuwania nieużywanego kodu z aplikacji][pruning]przez zmniejszenie ilości kodu, który jest dostarczany.
* *Ochrona integralności aplikacji*
  * Dodatkowe [zachowania obronne aplikacji][check-actions].
  * Możliwość podania okresu ostrzegawczego przed upływem ostatecznego terminu użytkowania aplikacji.
  * Możliwość powiadamiania kodu aplikacji w okresie ostrzegania o upływie okresu ważności lub po upływie terminu ostatecznego.

Dotfuscator Professional jest branżowym standardem [platformy .NET][net-obfuscator] , który jest przeznaczony dla deweloperów w przedsiębiorstwach, które wymagają ciągłego wsparcia, konserwacji i aktualizacji produktów.
Ponadto program Dotfuscator Professional oferuje ściślejszą integrację z programem Visual Studio i ma licencję na korzystanie z użytku komercyjnego.

Aby uzyskać więcej informacji na temat zaawansowanych funkcji ochrony aplikacji w programie Dotfuscator Professional, odwiedź [stronę omówienia Dotfuscator][product-about] rozwiązań z rozwiązaniami do zaawansowania i [porównaj ją z społecznością Dotfuscator][product-compare].
[W pełni obsługiwane wersje próbne są dostępne pod adresem PreEmptive.com][eval].

## <a name="see-also"></a>Zobacz też

[Ten artykuł znajduje się w pełnym podręczniku użytkownika Dotfuscator Community][full]

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