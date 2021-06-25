---
title: Implementowanie starszej wersji usługi językowej1 | Microsoft Docs
description: Dowiedz się, jak zaimplementować starszą usługę językową, która obsługuje rozszerzone funkcje usługi językowej, przy użyciu struktury pakietów zarządzanych (MPF). Część 1 z 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 34be4e54fbce413fe5ba916892216a9234d4ba93
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901152"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implementowanie starszej wersji usługi językowej 1
Za pomocą klas w programie Managed Package Framework (MPF) można zaimplementować starszą usługę językową, która obsługuje szeroką gamę funkcji, takich jak wyróżnianie składni, dopasowywanie nawiasów klamrowych i uzupełnianie intelliSense.

 Starsze usługi językowe są implementowane w ramach pakietów VSPackage, ale nowszą sposobem implementacji funkcji usługi językowej jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej na temat nowego sposobu implementowania usługi językowej, zobacz Editor and Language Service Extensions (Edytor [i rozszerzenia usługi językowej).](../../extensibility/editor-and-language-service-extensions.md)

> [!NOTE]
> Zalecamy jak najszybciej rozpocząć korzystanie z nowego interfejsu API edytora. Poprawi to wydajność usługi językowej i pozwoli korzystać z nowych funkcji edytora.

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)

 Omówienie funkcji usługi językowej obsługiwanych w pliku MPF.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Opisuje, co jest wymagane do zaimplementowania usługi językowej przy użyciu pliku MPF.

- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Opisuje kroki wymagane do zarejestrowania usługi językowej opartej na pliku MPF w usłudze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Opisuje dwa parsery, które są wymagane do zaimplementowania wszystkich funkcji usługi językowej przy użyciu pliku MPF.

- [Przewodnik: Tworzenie starszej wersji usługi językowej](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Zawiera podstawowe kroki, które są wymagane do zaimplementowania usługi językowej MPF w psłudze VSPackage.

- [Przewodnik: Pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Przedstawia techniki pobierania listy zainstalowanych fragmentów kodu.

- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)

 Zawiera linki do tematów, w których szczegółowo opisano, co należy zrobić, aby zaimplementować wszystkie funkcje usługi językowej przy użyciu pliku MPF.
