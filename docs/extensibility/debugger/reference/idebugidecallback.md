---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727828"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Umożliwia programowi Expression ewaluatora (EE) wyświetlanie komunikatu w oknie danych wyjściowych debugera.

## <a name="syntax"></a>Składnia

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 To wywołanie zwrotne jest implementowane przez zarządzany aparat debugowania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Może być używana przez ewaluatora wyrażeń do wysyłania danych wyjściowych do okna danych wyjściowych debugera.

## <a name="methods"></a>Metody
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Wysyła określony ciąg komunikatu do okna danych wyjściowych debugera.|

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
