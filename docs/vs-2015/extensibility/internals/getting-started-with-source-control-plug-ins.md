---
title: Wprowadzenie do wtyczek kontroli kodu źródłowego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85aa5727f252ad75c45064d7b885e3d282da36a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538164"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Wprowadzenie do wtyczek kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby utworzyć kontroli źródła wtyczek, należy utworzyć bibliotekę DLL, która implementuje funkcje zdefiniowane w interfejsie API wtyczki kontroli źródła, a następnie zarejestruj plik DLL za pomocą [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aby stał się dostępny do użytku w kontroli wersji kodu źródłowego.  
  
 Trzy wersje interfejsu API wtyczki kontroli źródła (w wersji 1.1 i 1.2, 1.3) są dostępne dla wtyczek kontroli kodu źródłowego. API wtyczki kontroli źródła opisane tutaj jest w wersji 1.3. Została zaprojektowana pod kątem pełnej zgodności z wtyczek kontroli kodu źródłowego obsługi wersji 1.1 i 1.2. [What's New in źródła kontrolki wtyczki interfejsu API w wersji 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) szczegółowo opisano nowe funkcje, które są obsługiwane w najnowszej wersji interfejsu API wtyczki kontroli źródła.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Instalowanie wtyczki kontroli źródła](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 W tym artykule opisano, jak utworzyć wpisy rejestru, które są wymagane do wtyczki kontroli źródła biblioteki DLL.  
  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Krótkie omówienie zmiany wprowadzone do interfejsu API wtyczki kontroli źródła w wersji 1.3.  
  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Krótkie omówienie zmiany wprowadzone do interfejsu API wtyczki kontroli źródła w wersji 1.2.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)  
 Zawiera pełną listę wszystkich elementów w interfejsie API wtyczki kontroli źródła.  
  
 [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definiuje zestaw SDK wtyczki kontroli źródła i opisuje dołączone zasoby.
