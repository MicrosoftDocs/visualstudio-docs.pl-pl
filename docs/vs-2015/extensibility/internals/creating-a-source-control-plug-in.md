---
title: Tworzenie wtyczki kontroli źródła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 37cb4cfc71b2574600bf7ca886c693b888ec821a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196966"
---
# <a name="creating-a-source-control-plug-in"></a>Tworzenie wtyczki kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zestaw Visual Studio SDK udostępnia zasoby, które umożliwiają dodawanie funkcji kontroli źródła do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE). Umożliwia korzystanie z dowolnych bibliotek DLL, które są zgodne z interfejsem API kontroli źródła opisanymi w tej dokumentacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Opisuje, jak zainstalować wtyczkę kontroli źródła i podświetlić obecnie dostępne wersje interfejsu API kontroli źródła.  
  
 [Architektura](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Używa diagramu architektury, aby wyjaśnić integrację wtyczki kontroli źródła z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Zawiera wskazówki dotyczące testowania instalacji i działania wtyczki kontroli źródła.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 W tym artykule omówiono sposób tworzenia pakietu VSPackage kontroli źródła, które nie tylko dostarczają funkcji kontroli źródła, ale zastępują [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejs użytkownika kontroli źródła.  
  
 [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)  
 Zawiera kompletną listę wszystkich elementów w interfejsie API dodatku plug-in kontroli źródła.  
  
 [Kontrola źródła](../../extensibility/internals/source-control.md)  
 W tym artykule omówiono opcje implementowania kontroli źródła jako funkcji zintegrowanej programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
