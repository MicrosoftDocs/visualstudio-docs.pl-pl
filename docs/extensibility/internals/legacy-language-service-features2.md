---
title: Starszej wersji usługi językowej2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de7e0fa6a229929a34ed3654c3a4e03e02d1129b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333506"
---
# <a name="legacy-language-service-features"></a>Funkcje usługi starszego języka
W poniższych sekcjach wymieniono niektóre funkcje usługi starszego języka, które można podać.

 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi języka, zobacz [edytora i rozszerzenia usługi w języka](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.

## <a name="in-this-section"></a>W tej sekcji
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Wyjaśnia sposób implementacji kolorowanie składni.

- [Formatowanie automatyczne w starszej wersji usługi językowej](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Wyjaśnia sposób implementacji, automatycznego formatowania.

- [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Wyjaśnia, jak zaimplementować etykietka informacji parametru funkcji IntelliSense.

- [Uzupełnianie instrukcji w starszej wersji usługi językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Wyjaśnia, jak wdrażać listy instrukcji IntelliSense i lista uzupełnianie składowych.

- [Zwijanie i tekst ukryty w starszej wersji usługi językowej](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Wyjaśnia sposób implementacji konspektu czy ukryty tekst.

- [Instrukcje: zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Wyjaśnia, niektóre kroki we wdrażaniu Obsługa debugera...

## <a name="related-sections"></a>Sekcje pokrewne