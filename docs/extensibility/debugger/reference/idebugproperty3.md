---
title: IDebugProperty3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2819724c204631112fd1a3e827126c4bc176972
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721043"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Ten interfejs zapewnia obsługę:

- Pobieranie dowolnie długi ciąg skojarzony z właściwością.

- Kojarzenie unikatowego identyfikatora z właściwością.

- Pobieranie listy niestandardowych widzów dla usługi.

- Ustawianie wartości właściwości z możliwością zgłaszania wszelkich wynikających z nich błędów

## <a name="syntax"></a>Składnia

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) w celu zapewnienia obsługi długich ciągów, identyfikatorów właściwości i niestandardowych widzów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na interfejsie, `IDebugProperty2` aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod dziedziczonych `IDebugProperty2`z `IDebugProperty3` , interfejs udostępnia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Zwraca długość ciągu skojarzonego z właściwością.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Zwraca ciąg w buforze dostarczonym przez użytkownika.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Tworzy unikatowy identyfikator dla tej właściwości.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Niszczy unikatowy identyfikator dla tej właściwości.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Zwraca liczbę niestandardowych widzów, z którymi można wyświetlać tę właściwość.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Zwraca listę niestandardowych widzów, z którymi można wyświetlać tę właściwość.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Ustawia wartość tej właściwości, zwracając komunikat o błędzie, jeśli coś poszło nie tak.|

## <a name="remarks"></a>Uwagi
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) jest preferowanym sposobem dla menedżera debugowania sesji (SDM), aby ustawić wartość właściwości.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
