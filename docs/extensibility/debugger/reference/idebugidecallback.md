---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5a489256b14b828fd548b3e2da3c2c02f9d5317
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349565"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

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