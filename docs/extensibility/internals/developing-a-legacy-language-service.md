---
title: Tworzenie usługi języka starszego | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708670"
---
# <a name="develop-a-legacy-language-service"></a>Tworzenie starszej usługi językowej
W tej sekcji znajdują się łącza do tematów ułatwiające tworzenie starszej usługi językowej.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi językowej, zobacz [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="in-this-section"></a>W tej sekcji
- [Model starszej usługi językowej](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Zapewnia model usługi języka minimalnego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dla edytora podstawowego. Tego modelu można użyć jako przewodnika do tworzenia własnej usługi języka.

- [Interfejsy usługi języka starszego języka](../../extensibility/internals/legacy-language-service-interfaces.md)

 W tym artykule omówiono obiekty wymagane do zaimplementowania usługi języka i zawiera listę dodatkowych obiektów, które można użyć do zapewnienia wyróżniania składni, dane metody i inne funkcje.

- [Przechwytywanie starszych poleceń usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 W tym artykule opisano sposób wstawiania filtru poleceń do usługi językowej w celu przechwycenia poleceń, które w przeciwnym razie obsłużyłyby widok tekstu.

- [Rejestrowanie starszej usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Zawiera informacje dotyczące sposobu rejestrowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usługi językowej przy użyciu programu .

- [Obsługa usługi językowej do debugowania](../../extensibility/internals/language-service-support-for-debugging.md)

 W tym artykule opisano, jak usługa języka może udostępniać funkcje do obsługi debugera.

- [Lista kontrolna: tworzenie starszej usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Zawiera instrukcje krok po kroku dotyczące tworzenia i integrowania usługi języka dla edytora podstawowego.

## <a name="related-sections"></a>Powiązane sekcje
- [Kolorowanie składni w starszej usłudze językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 W tym artykule omówiono sposób implementowania wyróżniania składni w usłudze języka.

- [Uzupełnianie instrukcji w starszej usłudze językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 W tym artykule omówiono ukończenie instrukcji, proces, w którym usługa języka pomaga użytkownikom zakończyć słowo kluczowe języka lub element, który rozpoczęli wpisywanie.

- [Informacje o parametrach w starszej usłudze językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 W tym artykule opisano, jak zapewnić wskazówki dotyczące metody przeciążonych funkcji i metod.

- [Jak: Zapewnienie obsługi ukrytego tekstu w starszej usłudze językowej](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Wyjaśnia cel regionu ukrytego tekstu i zawiera instrukcje dotyczące implementacji regionu ukrytego tekstu.

- [Jak: Zapewnienie rozszerzonej obsługi nakreślenia w starszej usłudze językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 W tym artykule wyjaśniono dwie opcje, które rozszerzają obsługę konspektów dla twojego języka poza obsługę polecenia *Zwiń do definicji.*
