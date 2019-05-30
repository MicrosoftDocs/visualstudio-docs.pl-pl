---
title: IDebugProperty3 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8581e8163ab95eac7d49c5deca70c339804aac64
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348700"
---
# <a name="idebugproperty3"></a>IDebugProperty3
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
 Wywołaj [QueryInterface](/cpp/atl/queryinterface) na `IDebugProperty2` interfejsu w celu uzyskania tego interfejsu.

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
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) jest preferowany sposób Menedżer debugowania sesji (SDM), aby ustawić wartości właściwości.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)