---
title: IDebugStackFrame2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719510"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Ten interfejs reprezentuje ramki pojedynczego stosu w stosie wywołań w określonym wątku.

## <a name="syntax"></a>Składnia

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania ramki stosu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [EnumFrameInfo,](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) aby pobrać interfejs [IEnumDebugFrameInfo2.](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Wywołanie [dalej,](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) aby pobrać strukturę `IDebugStackFrame2` [FRAMEINFO,](../../../extensibility/debugger/reference/frameinfo.md) która zawiera interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugStackFrame2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla tej ramki stosu.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla tej ramki stosu.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Pobiera nazwę ramki stosu.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Pobiera opis ramki stosu.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Pobiera zależną od komputera reprezentację zakresu adresów fizycznych skojarzonych z ramką stosu.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Pobiera kontekst oceny do wykonywania oceny wyrażenia w bieżącym kontekście ramki stosu i wątku.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Pobiera język skojarzony z ramką stosu.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Pobiera opis właściwości skojarzonych z ramką stosu.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Tworzy wyliczacz właściwości ramki stosu.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Pobiera wątku skojarzone z ramki stosu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest uzyskiwany tylko wtedy, gdy program debugowany został zatrzymany w punkcie przerwania (spowodowane przez punkt przerwania zestawu użytkownika lub wyjątek). Z tego interfejsu można uzyskać kontekst wyrażenia do oceny wyrażeń, można zwrócić listę rejestrów lub można uzyskać i zbadać stos wywołań.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
