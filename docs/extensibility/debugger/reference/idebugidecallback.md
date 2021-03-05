---
description: Umożliwia programowi Expression ewaluatora (EE) wyświetlanie komunikatu w oknie danych wyjściowych debugera.
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0ef2072967aad5f2cd012283b0c6f4ac7b9b3be
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172561"
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
