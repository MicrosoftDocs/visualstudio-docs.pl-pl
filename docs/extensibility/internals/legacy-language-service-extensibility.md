---
title: Rozszerzalność usługi starszego języka | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 339e23411f10e8cde32900feea4618c0806faacf
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645332"
---
# <a name="legacy-language-service-extensibility"></a>Rozszerzalność starszej wersji usługi językowej
Usługa języka obsługuje specyficzny dla języka do edycji kodu źródłowego w środowisku IDE.

 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi języka, zobacz [edytora i rozszerzenia usługi w języka](../../extensibility/editor-and-language-service-extensions.md).

 W tej sekcji omówiono struktury i implementacji starszej wersji usługi językowej.

## <a name="in-this-section"></a>W tej sekcji
- [Migrowanie starszej wersji usługi językowej](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Wyjaśnia, jak zaktualizować usługę języka z programu Visual Studio 2008 do najnowszej wersji.

- [Podstawowe informacje dotyczące starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-essentials.md)

 Zawiera ważne informacje dotyczące sposobu tworzenia usług językowych, nad zintegrowaniem język programowania Visual Studio.

- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)

 Zawiera łącza do tematów, które mogą pomóc Ci Tworzenie usługi języka.

- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Zawiera informacje dotyczące obsługi wyróżniania składni w ramach usługi w języka.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Zawiera informacje o tym, jak wdrożyć usługę w pełni funkcjonalne języka w kodzie zarządzanym przy użyciu środowiska pakietu zarządzanego (MPF).

- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 W tym artykule opisano, biblioteki i narzędzia umożliwiające przeglądanie widoków drzewa symboli w środowisku IDE.

## <a name="related-sections"></a>Sekcje pokrewne
- [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md)

 Zawiera omówienie edytory programu Visual Studio.

- [Obsługa usługi językowej do debugowania](../../extensibility/internals/language-service-support-for-debugging.md)

 Zapewnia informacje i łącza do programu Visual Studio debugowanie SDK, który zawiera informacje, które są wymagane do tworzenia i dostosowywania składniki debugera, używane do debugowania programów.