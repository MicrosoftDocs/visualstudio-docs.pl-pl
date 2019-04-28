---
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce4112addee78c4df293bf49e1cb191e4bbcd18b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868721"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Ten interfejs reprezentuje ramkę stosu w stosie wywołań, w szczególności wątku.

## <a name="syntax"></a>Składnia

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący ramkę stosu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) można pobrać [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfejsu. Wywołaj [dalej](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) można pobrać [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strukturę, która zawiera `IDebugStackFrame2` interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugStackFrame2`.

|Metoda|Opis|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla tej ramki stosu.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla tej ramki stosu.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Pobiera nazwę ramki stosu.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Pobiera opis ramki stosu.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Pobiera reprezentację zależnych od maszyny, zakresu adresów fizycznych skojarzonych z ramki stosu.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Pobiera kontekst oceny do wykonywania oceny wyrażenia w bieżącym kontekście ramki stosu i wątku.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Pobiera język ramki stosu.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Pobiera opis właściwości skojarzone z ramki stosu.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Tworzy moduł wyliczający stosu właściwości ramki.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Pobiera wątek skojarzony z ramki stosu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs otrzymuje tylko wtedy, gdy program poddawany został zatrzymany w punkcie przerwania (albo spowodowane przez użytkownika zestaw punktu przerwania lub wyjątku). W tym interfejsie kontekście wyrażenia można uzyskać można obliczyć wyrażenia, listę rejestrów, które mogą być zwracane lub stos wywołań, które mogą być uzyskane i badania.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)