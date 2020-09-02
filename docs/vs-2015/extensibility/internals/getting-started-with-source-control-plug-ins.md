---
title: Wprowadzenie z wtyczkami do kontroli źródła | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538164"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Wprowadzenie do wtyczek kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby utworzyć wtyczkę kontroli źródła, należy utworzyć bibliotekę DLL, która implementuje funkcje zdefiniowane w interfejsie API dodatku plug-in kontroli źródła, a następnie zarejestrować bibliotekę DLL w programie, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aby była dostępna do użycia w kontroli wersji kodu źródłowego.  
  
 Trzy wersje interfejsu API wtyczki kontroli źródła (wersje 1,1, 1,2 i 1,3) są dostępne dla wtyczek kontroli źródła. Interfejs API wtyczki kontroli źródła udokumentowany w tym miejscu jest w wersji 1,3. Została zaprojektowana tak, aby była w pełni zgodna z wtyczkami kontroli źródła obsługującymi wersje 1,1 i 1,2. Sekcja [co nowego w interfejsie API dodatku plug-in kontroli źródła w wersji 1,3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) zawiera szczegółowe informacje o nowych funkcjach obsługiwanych w najnowszej wersji interfejsu API wtyczki kontroli źródła.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Opisuje sposób tworzenia wpisów rejestru wymaganych do podłączenia do biblioteki DLL kontroli źródła.  
  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Zawiera krótkie omówienie zmian wprowadzonych w interfejsie API dodatku plug-in kontroli źródła w wersji 1,3.  
  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Zawiera krótkie omówienie zmian wprowadzonych w interfejsie API dodatku plug-in kontroli źródła w wersji 1,2.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)  
 Zawiera kompletną listę wszystkich elementów w interfejsie API dodatku plug-in kontroli źródła.  
  
 [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definiuje zestaw SDK wtyczki kontroli źródła i opisuje uwzględnione zasoby.
