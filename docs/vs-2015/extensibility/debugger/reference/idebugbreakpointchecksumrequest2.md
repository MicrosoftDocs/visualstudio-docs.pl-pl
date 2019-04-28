---
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d06656ba05c3356d9f2a148045adbf4538c5ae5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431618"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reprezentuje dokument sumy kontrolnej dla żądania punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Zaimplementowane przez [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pakiet debugowania i używane przez aparaty debugowania.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugBreakpointChecksumRequest2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Pobiera suma kontrolna dokumentu żądania punktu przerwania podane Unikatowy identyfikator algorytmu sumy kontrolnej do użycia.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Określa, czy suma kontrolna jest włączone dla tego dokumentu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
