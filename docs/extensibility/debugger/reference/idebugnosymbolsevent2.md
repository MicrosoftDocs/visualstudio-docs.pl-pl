---
title: IDebugNoSymbolsEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 179d8a95bc54db90a98311626b34c3e17b68f7f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873122"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Sygnały [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugera interfejsu użytkownika, aby ostrzec użytkownika, że symbole nie można zlokalizować dla uruchomionego pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Implementowany przez aparaty debugowania i używane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugera interfejsu użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll