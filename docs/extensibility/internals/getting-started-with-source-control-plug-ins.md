---
title: Wprowadzenie do wtyczek kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efc21e07830614d9d3041b2d2d231fd82c652114
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708346"
---
# <a name="get-started-with-source-control-plug-ins"></a>Wprowadzenie do wtyczek kontroli źródła
Aby utworzyć wtyczkę formantu źródła, należy utworzyć bibliotekę DLL, która implementuje funkcje zdefiniowane w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsie API wtyczki kontroli źródła, a następnie zarejestrować bibliotekę DLL, aby udostępnić ją do użycia w kontroli wersji kodu źródłowego.

 Trzy wersje interfejsu API dodatku Plug-in dodatku Source Control (wersje 1.1, 1.2 i 1.3) są dostępne dla wtyczek kontroli źródła. Udokumentowany w tym miejscu interfejs API wtyczki kontroli źródła jest w wersji 1.3. Został zaprojektowany tak, aby był w pełni kompatybilny z wtyczkami kontroli źródła obsługującymi wersje 1.1 i 1.2. Co nowego w sekcji [Wtyczka interfejsu API dodatku 1.3 wtyczki kontroli źródła w wersji 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) wyszczepuje nowe funkcje obsługiwane w najnowszej wersji interfejsu API wtyczki kontroli źródła.

## <a name="in-this-section"></a>W tej sekcji
- [Jak: Instalowanie wtyczki kontroli źródła](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 W tym artykule opisano sposób tworzenia wpisów rejestru, które są wymagane do podłączenia biblioteki DLL formantu źródła.

- [Co nowego w interfejsie API wtyczki kontroli źródła w wersji 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Zawiera krótkie omówienie zmian wprowadzonych w interfejsie API dodatku dodatku Dodatku Kontroli źródła w wersji 1.3.

- [Co nowego w interfejsie API wtyczki kontroli źródła w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Zawiera krótkie omówienie zmian wprowadzonych w interfejsie API dodatku dodatku Dodatku Kontroli źródła w wersji 1.2.

## <a name="related-sections"></a>Powiązane sekcje
- [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)

 Zawiera pełną listę wszystkich elementów w interfejsie API wtyczki kontroli źródła.

- [Tworzenie wtyczki formantu źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Definiuje sdk wtyczki kontroli źródła i opisuje dołączone zasoby.
