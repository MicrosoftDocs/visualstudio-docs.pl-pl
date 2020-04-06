---
title: Implementowanie usługi języka starszego1 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707699"
---
# <a name="implementing-a-legacy-language-service"></a>Implementowanie starszej wersji usługi językowej
Klasy w ramach pakietu zarządzanego (MPF) można użyć do zaimplementowania usługi języka starszego, który obsługuje szeroką gamę funkcji, takich jak wyróżnianie składni, dopasowywanie nawiasów klamrowych i zakończenie IntelliSense.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi językowej, zobacz [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)

 Omówienie funkcji usługi języka, które są obsługiwane w MPF.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 W tym artykule opisano, co jest wymagane do zaimplementowania usługi języka przy użyciu mpf.

- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)

 W tym artykule opisano kroki, które są wymagane [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]do zarejestrowania usługi języka opartej na mpf w pliku .

- [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 W tym artykule opisano dwa analizatory, które są wymagane do zaimplementowania wszystkich funkcji usługi języka przy użyciu MPF.

- [Przewodnik: tworzenie starszej wersji usługi językowej](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Zawiera podstawowe kroki, które są wymagane do zaimplementowania usługi języka MPF w vsPackage.

- [Przewodnik: pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Demonstruje techniki pobierania listy urywków kodu zainstalowanego.

- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)

 Zawiera łącza do tematów, które szczegółowo, co należy zrobić, aby zaimplementować wszystkie funkcje usługi języka przy użyciu mpf.
