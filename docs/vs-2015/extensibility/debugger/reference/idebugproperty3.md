---
title: IDebugProperty3 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 479827cc83486d6bb9c68d0749b8870cd6c41861
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694764"
---
# <a name="idebugproperty3"></a>IDebugProperty3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs zapewnia obsługę:  
  
- Pobieranie długi ciąg skojarzony z właściwością.  
  
- Kojarzenie Unikatowy identyfikator z właściwością.  
  
- Pobiera listę przeglądarek niestandardowych właściwości.  
  
- Ustawienie wartości właściwości z możliwością zgłosić wszystkie wynikowe błędy  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) celu zapewnienia obsługi długich ciągów, identyfikatory właściwości i przeglądarek niestandardowych.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na `IDebugProperty2` interfejsu w celu uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod odziedziczone `IDebugProperty2`, `IDebugProperty3` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Zwraca długość ciągu skojarzonego z właściwością.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Zwraca ciąg w buforze dostarczone przez użytkownika.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Tworzy unikatowy identyfikator dla tej właściwości.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Niszczy Unikatowy identyfikator dla tej właściwości.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Zwraca liczbę przeglądarek niestandardowych, które tej właściwości można wyświetlić w programie.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Zwraca listę przeglądarek niestandardowych, które tej właściwości można wyświetlić w programie.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Ustawia wartość tej właściwości, zwraca komunikat o błędzie, jeśli coś poszło nie tak.|  
  
## <a name="remarks"></a>Uwagi  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) jest preferowany sposób Menedżer debugowania sesji (SDM), aby ustawić wartości właściwości.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
