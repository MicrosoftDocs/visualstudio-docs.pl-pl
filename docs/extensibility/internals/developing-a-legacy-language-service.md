---
title: Opracowywanie starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się więcej na temat implementowania starszej wersji usługi językowej w ramach programu pakietu VSPackage lub za pomocą rozszerzeń Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f7876b590cb5b09cf5db571ba1145f6bf747e5e5
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329747"
---
# <a name="develop-a-legacy-language-service"></a>Opracowywanie starszej wersji usługi językowej
Ta sekcja zawiera linki do tematów, które ułatwiają tworzenie starszej wersji usługi językowej.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi językowej, zobacz [edytory i rozszerzenia usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="in-this-section"></a>W tej sekcji
- [Model starszej wersji usługi językowej](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Oferuje model minimalnej usługi językowej dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podstawowego edytora. Ten model służy jako przewodnik tworzenia własnej usługi językowej.

- [Starsze interfejsy usługi językowej](../../extensibility/internals/legacy-language-service-interfaces.md)

 Omawia obiekty wymagane do zaimplementowania usługi językowej oraz zawiera listę dodatkowych obiektów, których można użyć w celu zapewnienia wyróżniania składni, danych metod i innych funkcji.

- [Przechwycenie starszych poleceń usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Opisuje sposób wstawiania filtru poleceń do usługi językowej w celu przechwycenia poleceń, które w przeciwnym razie mógłby obsłużyć widok tekstu.

- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Zawiera informacje dotyczące sposobu rejestrowania usługi językowej przy użyciu programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Obsługa debugowania przez usługę języka](../../extensibility/internals/language-service-support-for-debugging.md)

 Opisuje, w jaki sposób usługa języka może udostępniać funkcje do obsługi debugera.

- [Lista kontrolna: Tworzenie starszej wersji usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Zawiera instrukcje krok po kroku dotyczące tworzenia i integrowania usługi językowej dla edytora podstawowego.

## <a name="related-sections"></a>Sekcje pokrewne
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 W tym artykule omówiono sposób implementacji wyróżniania składni w usłudze językowej.

- [Uzupełnianie instrukcji w starszej wersji usługi językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Omawia uzupełnianie instrukcji, proces, za pomocą którego usługa języka ułatwia użytkownikom zakończenie słowa kluczowego języka lub elementu, który rozpoczął wpisywanie.

- [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Opisuje, w jaki sposób zapewnić porady dotyczące metod dla przeciążonych funkcji i metod.

- [Instrukcje: zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Wyjaśnia przeznaczenie obszaru tekstu ukrytego i zawiera instrukcje dotyczące implementowania ukrytego obszaru tekstu.

- [Instrukcje: zapewnianie rozszerzonej obsługi konspektu w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Wyjaśnia dwie opcje, które zwiększają obsługę tworzenia konspektów dla języka poza obsługą polecenia *Zwiń do definicji* .
