---
title: IDebugParsedExpression | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6fb6159150013e0f17d282efdd5ec37925d57f61
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786715"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs reprezentuje wyrażenie przeanalizowany, gotowy do obliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluatora wyrażeń implementuje ten interfejs do reprezentowania przeanalizowany wyrażenie, które jest gotowe do oceny.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zwraca ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugParsedExpression`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Oblicza wyrażenie przeanalizowany.|  
  
## <a name="remarks"></a>Uwagi  
 Jeżeli obiekt wywołujący jest gotowy do obliczenia wyrażenia, wywołuje [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) do zwrócenia [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) zawierającą wynik obliczenia. Takie podejście legalną dwuczęściową do oceny, analizowanie, a następnie ocenę, umożliwia przeanalizowany wyrażenie do obliczenia wiele razy, z pominięciem czasochłonnym procesem analizowania wyrażenia.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Analizy](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
