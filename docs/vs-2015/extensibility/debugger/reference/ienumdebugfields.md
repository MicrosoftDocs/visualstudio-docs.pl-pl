---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e3c9a43b6903522fe2caf0e329f8e8faa69cd6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161092"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje kolekcję obiektów implementujących interfejs [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawcę symboli w celu udostępniania zestawów obiektów implementujących interfejs [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Należy zauważyć, że nie jest to standardowe wyliczenie COM z powodu obecności metody [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) .  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest zwracany przez [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) i [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 Ten interfejs implementuje następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Pobiera następny zestaw obiektów [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) z wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Pomija określoną liczbę wpisów.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Resetuje Wyliczenie do pierwszego wpisu.|  
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Pobiera kopię bieżącego wyliczania.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawcy symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
