---
title: Tworzenie starszej wersji usługi językowej | Dokumentacja firmy Microsoft
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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a4cbc68e84c6593ca61be9234fcec3e88f3f333
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631877"
---
# <a name="develop-a-legacy-language-service"></a>Tworzenie starszej wersji usługi językowej
Sekcja Łącze do tematów, które ułatwiają tworzenie starszej wersji usługi językowej.

 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi języka, zobacz [Edytor i język rozszerzenia usługi](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.

## <a name="in-this-section"></a>W tej sekcji
- [Model starszej wersji usługi językowej](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Udostępnia model usługi minimalny języka na potrzeby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] edytorze podstawowych funkcji. Ten model jako przewodnik służy do tworzenia usługi języka.

- [Interfejsy usługi starszego języka](../../extensibility/internals/legacy-language-service-interfaces.md)

 Omówiono obiekty wymagane do wykonania usługi językowej i listę dodatkowe obiekty, które służy do wyróżniania składni, Metoda danych i innych funkcji.

- [Przechwytywanie poleceń usługi starszego języka](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Opisuje sposób wstawić filtr polecenia do usługi języka do poleceń intercept, które widoku tekstu w przeciwnym razie będzie obsługiwać.

- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Zawiera informacje o tym, jak zarejestrować usługi w języka przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Obsługa usługi językowej do debugowania](../../extensibility/internals/language-service-support-for-debugging.md)

 W tym artykule opisano, jak usługa języka może zapewnić funkcji obsługi debugera.

- [Lista kontrolna: Tworzenie starszej wersji usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Instrukcje krok po kroku dotyczące tworzenia i integrowania usługi języka dla podstawowy edytor.

## <a name="related-sections"></a>Sekcje pokrewne
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 W tym artykule omówiono sposób implementacji, wyróżnianie składni w usłudze języka.

- [Uzupełnianie instrukcji w starszej wersji usługi językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 W tym artykule omówiono uzupełniania instrukcji, proces, za pomocą którego usługa języka ułatwiają zakończyć słowem kluczowym języka lub element, który zostały uruchomione, wpisując.

- [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 W tym artykule opisano, jak zapewnić porady metodę dla przeciążonej funkcji i metod.

- [Instrukcje: Zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Zawiera wyjaśnienie przeznaczenia obszaru tekstu ukrytego i zawiera instrukcje dotyczące sposobu implementacji region tekstu ukrytego.

- [Instrukcje: Zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Opisano dwie opcje, które rozszerzają obsługi zwijania dla danego języka, poza obsługi *Zwiń do definicji* polecenia.