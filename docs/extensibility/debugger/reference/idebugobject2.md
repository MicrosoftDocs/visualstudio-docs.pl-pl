---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5712187bf5ea945a806b1baa91310be13f70eada
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971796"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs zapewnia dodatkowe informacje na temat obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń implementuje ten interfejs, oferującej obsługę aliasów i dostęp do informacji o obiekcie.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu można uzyskać ten interfejs, za pomocą [QueryInterface](/cpp/atl/queryinterface). Ponadto [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) zwraca ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod na [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu `IDebugObject2` interfejsu wykonuje następujące czynności:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Pobiera pola lub zmiennej (jeśli istnieje), mogą tworzyć kopię właściwość reprezentowany przez ten obiekt.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Pobiera kod zarządzany obiekt reprezentujący wartość tego obiektu.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Tworzy unikatowy identyfikator dla tego obiektu lub zwraca istniejącego aliasu.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Pobiera alias skojarzony z tym obiektem, jeśli istnieje.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Pobiera typ tego obiektu.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Określa, czy ten obiekt reprezentuje dane użytkownika.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Określa, czy stan Edytuj i Kontynuuj nie jest już prawidłowy.<br /><br /> Ewaluator wyrażeń niestandardowych nie obsługuje tej metody (zawsze powinna zwrócić `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) do dyskusji na temat aliasów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)