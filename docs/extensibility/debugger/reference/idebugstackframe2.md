---
description: Ten interfejs reprezentuje pojedynczą ramkę stosu w stosie wywołań w określonym wątku.
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5ec53e89afb43187c641058620df53c4a61d6cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145914"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Ten interfejs reprezentuje pojedynczą ramkę stosu w stosie wywołań w określonym wątku.

## <a name="syntax"></a>Składnia

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować ramkę stosu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) , aby pobrać Interfejs [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) . Połącz się [dalej](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) , aby pobrać strukturę [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) , która zawiera `IDebugStackFrame2` interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugStackFrame2` .

|Metoda|Opis|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla tej ramki stosu.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla tej ramki stosu.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Pobiera nazwę ramki stosu.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Pobiera opis ramki stosu.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Pobiera reprezentację zakresu adresów fizycznych skojarzonych z ramką stosu w zależności od maszyny.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Pobiera kontekst oceny służący do obliczania wyrażenia w bieżącym kontekście ramki stosu i wątku.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Pobiera język skojarzony z ramką stosu.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Pobiera opis właściwości skojarzonych z ramką stosu.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Tworzy moduł wyliczający dla właściwości ramki stosu.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Pobiera wątek skojarzony z ramką stosu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest uzyskiwany tylko wtedy, gdy debugowany program został zatrzymany w punkcie przerwania (spowodowanym przez punkt przerwania lub wyjątek). Z tego interfejsu można uzyskać kontekst wyrażenia do obliczania wyrażeń, listę rejestrów może zostać zwrócona lub można uzyskać i zbadać stos wywołań.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
