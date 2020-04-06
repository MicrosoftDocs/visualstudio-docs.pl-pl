---
title: IDebugIDECallback | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727828"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Umożliwia ewaluatorowi wyrażeń (EE) wyświetlanie komunikatu w oknie wyjściowym debugera.

## <a name="syntax"></a>Składnia

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 To wywołanie zwrotne jest implementowane przez aparat debugowania zarządzanego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Może być zużywany przez oceniającego wyrażenie, aby wysłać dane wyjściowe do okna wyjściowego debugera.

## <a name="methods"></a>Metody
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[Komunikat DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Wysyła określony ciąg komunikatu do okna wyjściowego debugera.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
