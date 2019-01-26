---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bb2f2b35865f423b4405738260976ab19308eab
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920672"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Ten interfejs zapewnia dostęp do Identyfikatora procesu, który jest właścicielem obiektu, którego adres jest reprezentowany przez ten interfejs.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu. Ten interfejs zapewnia dostęp do Identyfikatora procesu, który jest właścicielem obiektu, który jest powiązany z tym adresem.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w vtable kolejności  
 Oprócz metod odziedziczone [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu, ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Pobiera identyfikator procesu, który jest właścicielem obiektu reprezentowanego przez ten interfejs.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawca symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)