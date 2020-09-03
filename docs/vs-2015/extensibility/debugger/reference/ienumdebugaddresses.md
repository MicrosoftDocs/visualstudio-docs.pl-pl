---
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2373a26da1f6c3b327bea3a6f2402beb7d8bce45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196137"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje kolekcję obiektów implementujących interfejs [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawcę symboli w celu udostępniania zestawów obiektów implementujących interfejs [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Należy zauważyć, że nie jest to standardowe wyliczenie COM z powodu obecności metody [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) .  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest zwracany przez [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) i [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 Ten interfejs implementuje następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Pobiera następny zestaw obiektów [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) z wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Pomija określoną liczbę wpisów.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Resetuje Wyliczenie do pierwszego wpisu.|  
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Pobiera kopię bieżącego wyliczania.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest zwykle używany przez aparat debugowania w celu określenia odpowiedniego adresu do przekazania do ewaluatora wyrażeń.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawcy symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
