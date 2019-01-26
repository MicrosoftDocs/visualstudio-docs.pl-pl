---
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cc708bf5505a696c3797a66daa9eeab7402ccd6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935257"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Zezwala na wykonanie zapytania dotyczącego informacji o komputerze docelowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez port obiektów Menedżer debugowania sesji.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugWindowsComputerPort2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Pobiera informacje o komputerze, na którym w debugerze programu uruchomione.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll