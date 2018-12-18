---
title: IDebugStackFrame2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc6a6ea1b1d864c3f14158b9687181e6bdb6bc4a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816674"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)

