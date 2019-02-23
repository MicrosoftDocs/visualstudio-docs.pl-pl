---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58684cc5139d2797a08b74d9c0309252141e2498
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723399"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Umożliwia ewaluatora wyrażeń (EE) wyświetlić komunikat w oknie danych wyjściowych debugera.

## <a name="syntax"></a>Składnia

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 To wywołanie zwrotne jest implementowany przez aparat debugowania zarządzanego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Mogą być używane przez ewaluatora wyrażeń, aby wysłać dane wyjściowe do okna danych wyjściowych debugera.

## <a name="methods"></a>Metody
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Wysyła ciągu określony komunikat do okna danych wyjściowych debugera.|

## <a name="requirements"></a>Wymagania
 Nagłówek: EE.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll