---
title: IDebugExpressionEvaluator2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f11bab918dc6cc95504b23d3c42c7ffdcf3e0a9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413959"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Reprezentuje rozbudowaną wersją ewaluatora wyrażeń (EE).

## <a name="syntax"></a>Składnia

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez ewaluatora wyrażeń.

## <a name="methods"></a>Metody
 Oprócz metod na [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfejsu, ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Pobiera obiekt usługi, na podstawie jego unikatowy identyfikator.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Wstępnie ładuje moduły wyznaczony przez dostawcę określonego symbolu.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Umożliwia Ewaluator wyrażeń (EE) określić interfejs wywołania zwrotnego, który aparat debugera (DE) będzie używany do odczytu ustawienia metryki.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Ustawia ścieżkę do wykonywalnych języka wspólnego (CLR) załadowane w debugerze.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Umożliwia to aparat debugowania do przekazania wywołanie zwrotne do Ewaluator wyrażeń podczas inicjowania.|
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Zatrzymuje i czyści Ewaluator wyrażeń.|

## <a name="requirements"></a>Wymagania
 Nagłówek: EE.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll