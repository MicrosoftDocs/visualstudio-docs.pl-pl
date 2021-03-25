---
title: IDebugProperty3 | Microsoft Docs
description: Ten interfejs zapewnia obsługę pobierania długiej długości ciągu skojarzonego z właściwością, kojarzenia unikatowego identyfikatora z właściwością, pobierając listę niestandardowych podglądów dla właściwości, ustawiając wartość właściwości z możliwością zgłaszania błędów.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 933810ac5b1e0ba34edf7cfe8d4303180c862fe2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083911"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Ten interfejs zapewnia wsparcie dla:

- Pobieranie arbitralnie długiego ciągu skojarzonego z właściwością.

- Kojarzenie unikatowego identyfikatora z właściwością.

- Pobieranie listy niestandardowych podglądów dla właściwości.

- Ustawianie wartości właściwości z możliwością raportowania wszelkich błędów powstających

## <a name="syntax"></a>Składnia

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs w tym samym obiekcie, który implementuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , aby zapewnić obsługę długich ciągów, identyfikatorów właściwości i podglądów niestandardowych.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj metodę [QueryInterface](/cpp/atl/queryinterface) na `IDebugProperty2` interfejsie, aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod dziedziczonych z `IDebugProperty2` , `IDebugProperty3` Interfejs udostępnia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Zwraca długość ciągu skojarzonego z właściwością.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Zwraca ciąg w buforze dostarczonym przez użytkownika.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Tworzy unikatowy identyfikator dla tej właściwości.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Niszczy unikatowy identyfikator dla tej właściwości.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Zwraca liczbę niestandardowych podglądów, z którymi ta właściwość może być wyświetlana.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Zwraca listę niestandardowych podglądów, z którymi ta właściwość może być wyświetlana.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Ustawia wartość tej właściwości, zwracając komunikat o błędzie, jeśli wystąpił problem.|

## <a name="remarks"></a>Uwagi
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) jest preferowanym sposobem ustawienia wartości właściwości przez Menedżera debugowania sesji (SDM).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
