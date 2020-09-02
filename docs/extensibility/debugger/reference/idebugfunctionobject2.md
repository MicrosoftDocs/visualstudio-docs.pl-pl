---
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4150480d2e6686992d78727b6fed817da270145
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728432"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Reprezentuje funkcję i ulepsza Interfejs [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="syntax"></a>Składnia

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń (EE) implementuje ten interfejs, aby reprezentować funkcję.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Metody tego interfejsu opóźniają te **IDebugFunctionObject** w następujący sposób:

- Metoda **IDebugEvaluate** przyjmuje flagi.

- Metoda **CreateObject** przyjmuje flagi i przekroczenie limitu czasu.

- Metoda **CreateStringObjectWithLength** ma długość.

## <a name="methods"></a>Metody
 Ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Tworzy obiekt, który używa konstruktora danego ustawienia flagi oceny i wartości limitu czasu.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Tworzy obiekt String o określonej długości.|
|[Oceny](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Wywołuje funkcję i zwraca wynikową wartość jako obiekt.|

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
