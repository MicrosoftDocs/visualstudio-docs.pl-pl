---
title: IDebugMemoryBytes2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddbe101efe069787bbbb2ad6462c87bc1151c0cd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751958"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje bajtów pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania bajtów w pamięci.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) zwraca ten interfejs, w celu zapewnienia dostępu do pamięci systemowej. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) i [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) zwraca ten interfejs, aby zapewnić dostęp do obiektu w bajtach.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugMemoryBytes2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Odczytuje sekwencji bajtów, zaczynając od danej lokalizacji.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Zapisuje `dwCount` bajty począwszy `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Pobiera rozmiar w bajtach, pamięci, reprezentowane przez ten interfejs.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku właściwości [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) udostępnia interfejs reprezentujący tablicę `IDebugMemoryBytes2` interfejsu, aby uzyskać dostęp do wartości w tablicy.  
  
 Visual Studio **widok pamięci** wywołania [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) można pobrać `IDebugMemoryBytes2` interfejs do uzyskiwania dostępu do pamięci systemowej. Adres, który ma być uzyskiwany dostęp jest uzyskiwany analizowania wyrażenia jako adres zawierana widok pamięci, a następnie dokonanie oceny oprogramowania przy użyciu wyrażenia przeanalizowany [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) można pobrać `IDebugProperty2` interfejsu. Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) zwraca [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) adres pamięci, który opisuje. Ten kontekst pamięci jest następnie przekazywany do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

