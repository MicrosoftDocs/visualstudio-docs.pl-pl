---
title: Rozszerzalność starszej wersji usługi językowej | Microsoft Docs
description: Zapoznaj się ze strukturą, implementacją i rozszerzalnością starszych usług językowych w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f22d6997d932884e5aeb8d794b7884b40a8d5dab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074499"
---
# <a name="legacy-language-service-extensibility"></a>Rozszerzalność starszej wersji usługi językowej
Usługa języka zapewnia obsługę specyficzną dla języka na potrzeby edytowania kodu źródłowego w środowisku IDE.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi językowej, zobacz [edytory i rozszerzenia usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

 W tej sekcji omówiono strukturę i implementację starszej wersji usługi językowej.

## <a name="in-this-section"></a>W tej sekcji
- [Migrowanie starszej wersji usługi językowej](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Wyjaśnia, jak zaktualizować usługę języka z programu Visual Studio 2008 do najnowszej wersji.

- [Podstawowe informacje dotyczące starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-essentials.md)

 Zawiera ważne informacje dotyczące sposobu tworzenia usług językowych w celu integracji języka programowania z programem Visual Studio.

- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)

 Zawiera łącza do tematów, które mogą pomóc w tworzeniu usługi językowej.

- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Zawiera informacje na temat obsługi wyróżniania składni w usłudze językowej.

- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Zawiera informacje dotyczące sposobu korzystania z struktury pakietu zarządzanego (MPF) w celu zaimplementowania w pełni funkcjonalnej usługi językowej w kodzie zarządzanym.

- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Opisuje biblioteki i narzędzia, które umożliwiają przeglądanie widoków drzewa symboli w IDE.

## <a name="related-sections"></a>Sekcje pokrewne
- [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md)

 Zawiera omówienie edytorów programu Visual Studio.

- [Obsługa usługi językowej do debugowania](../../extensibility/internals/language-service-support-for-debugging.md)

 Zawiera informacje i link do zestawu SDK debugowania programu Visual Studio, który zawiera informacje wymagane do tworzenia i dostosowywania składników debugera używanych do debugowania programów.
