---
title: IDebugObject2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726078"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs zawiera dodatkowe informacje o obiekcie.

## <a name="syntax"></a>Składnia

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Oceniający wyrażenie implementuje ten interfejs, aby oferować obsługę aliasów i dostęp do informacji o obiekcie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) można uzyskać ten interfejs za pomocą [QueryInterface](/cpp/atl/queryinterface). Ponadto [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod na interfejsie [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) `IDebugObject2` interfejs implementuje następujące czynności:

|Metoda|Opis|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Pobiera pole lub zmienną (jeśli istnieje), które mogą być kopii zapasowej właściwości reprezentowane przez ten obiekt.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Pobiera obiekt kodu zarządzanego reprezentujący wartość tego obiektu.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Tworzy unikatowy identyfikator dla tego obiektu lub zwraca istniejący alias.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Pobiera alias skojarzony z tym obiektem, jeśli istnieje.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Pobiera typ tego obiektu.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Określa, czy ten obiekt reprezentuje dane użytkownika.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Określa, czy stan Edytuj i Kontynuuj nie jest już prawidłowy.<br /><br /> Oceniający wyrażenie niestandardowe nie implementuje tej `E_NOTIMPL`metody (zawsze powinna zwracać).|

## <a name="remarks"></a>Uwagi
 Zobacz [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) do dyskusji na temat aliasów.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
