---
title: Implementowanie starszej wersji językowej Service1 | Microsoft Docs
description: Dowiedz się, jak zaimplementować starszą wersję usługi językowej, która obsługuje rozszerzone funkcje usługi językowej przy użyciu struktury pakietu zarządzanego (MPF). Część 1 z 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99e3f11a9ea60595b2372921702282c2bb4d8dcd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085913"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implementowanie starszej wersji usługi językowej 1
Klasy w strukturze pakietów zarządzanych (MPF) mogą służyć do implementowania starszej wersji usługi językowej, która obsługuje szeroką gamę funkcji, takich jak wyróżnianie składni, dopasowywanie nawiasów klamrowych i uzupełnianie IntelliSense.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi językowej, zobacz [edytory i rozszerzenia usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)

 Omówienie funkcji usługi językowej, które są obsługiwane w programie MPF.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Opisuje, co jest wymagane do zaimplementowania usługi językowej przy użyciu MPF.

- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Zawiera opis czynności, które są wymagane do zarejestrowania usługi językowej opartej na MPF [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Opisuje dwa analizatory, które są wymagane do zaimplementowania wszystkich funkcji usługi językowej przy użyciu MPF.

- [Przewodnik: Tworzenie starszej wersji usługi językowej](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Zawiera podstawowe kroki, które są wymagane do zaimplementowania usługi języka MPF w pakietu VSPackage.

- [Przewodnik: Pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Demonstruje techniki pobierania listy zainstalowanych fragmentów kodu.

- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)

 Zawiera łącza do tematów zawierających szczegółowe informacje o tym, co należy zrobić, aby zaimplementować wszystkie funkcje usługi językowej przy użyciu MPF.
