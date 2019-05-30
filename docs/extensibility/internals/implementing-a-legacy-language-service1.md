---
title: Implementowanie starszej wersji usługi językowej1 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 626838b0e82846f66b817465fca2df353af42dd5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315647"
---
# <a name="implementing-a-legacy-language-service"></a>Implementowanie starszej wersji usługi językowej
Klas środowiska pakietu zarządzanego (MPF) można użyć do wdrożenia usługi starszego języka, który obsługuje szeroką gamę funkcji, takich jak wyróżnianie składni, parowanie nawiasów klamrowych i uzupełnianie przez funkcję IntelliSense.

 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi języka, zobacz [edytora i rozszerzenia usługi w języka](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)

 Omówienie funkcji usługi języka, które są obsługiwane w MPF.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 W tym artykule opisano, co jest wymagane do wdrożenia usługi językowej przy użyciu MPF.

- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)

 W tym artykule opisano kroki, które są wymagane do zarejestrowania usługi języka opartego na MPF z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 W tym artykule opisano dwa analizatory składni, które są wymagane do wdrożenia wszystkich funkcji wersji usługi językowej przy użyciu MPF.

- [Przewodnik: tworzenie starszej wersji usługi językowej](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Zawiera podstawowe kroki, które są wymagane do wdrożenia usługi w języka MPF w VSPackage.

- [Przewodnik: pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Pokazuje technik pobieranie listy zainstalowanych fragmentów kodu.

- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)

 Zawiera łącza do tematów w tym szczegółów, co należy zrobić, aby zaimplementować wszystkie funkcje usługi w języka przy użyciu MPF.