---
title: IEnumDebugFrameInfo2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716608"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Ten interfejs wylicza struktury [FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

## <a name="syntax"></a>Składnia

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby zapewnić listę struktur, która opisuje bieżący stos wywołań.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Visual Studio wywołuje [EnumFrameInfo,](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) aby uzyskać ten interfejs, gdy punkt przerwania, wyjątek lub zatrzymanie występuje w programie debugowanym.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IEnumDebugFrameInfo2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Pobiera określoną liczbę struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) w sekwencji wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Pomija określoną liczbę struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) w sekwencji wyliczenia.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Resetuje sekwencję wyliczenia do początku.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Pobiera liczbę [frameinfo](../../../extensibility/debugger/reference/frameinfo.md) struktur w wyliczacza.|

## <a name="remarks"></a>Uwagi
 Visual Studio uzyskuje ten interfejs jako pierwszy krok do obsługi punktu przerwania, wyjątku lub przerwy generowane przez użytkownika w programie debugowane. Lista struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) reprezentuje bieżący stos wywołań, z bieżącym wywołaniem funkcji na początku listy i najstarszym wywołaniem funkcji na końcu listy. Każdy `FRAMEINFO` reprezentuje ramkę stosu, kontekst, w którym wyrażenia mogą być oceniane i zmienne lokalne spojrzał.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
