---
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd11e57c8e2ec03da1dcfa9ff76b3b3ec2ded5e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149304"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Umożliwia wykonywanie zapytań dotyczących informacji o komputerze docelowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez obiekty portów Menedżera debugowania sesji.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugWindowsComputerPort2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Pobiera informacje o komputerze, na którym działa debuger.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
