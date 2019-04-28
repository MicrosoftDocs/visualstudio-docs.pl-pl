---
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e89d7fcb33441aeb2a52218d8d74ac4dd98e4b3d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413771"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje obiekt, który tworzy obiekt wiążący, do hermetyzacji wartości symboli i wyrażeń.

## <a name="syntax"></a>Składnia

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs reprezentujący obiekt.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest klasą bazową dla wszystkich obiektów używanych przez ewaluatora wyrażeń w wyrażeniach przeanalizowany. Jest on zwracany przez wywołanie [powiązać](../../../extensibility/debugger/reference/idebugbinder-bind.md) metody. [QueryInterface](/cpp/atl/queryinterface) uzyskuje bardziej wyspecjalizowane interfejsy, w tym interfejsie.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugObject`.

|Metoda|Opis|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Pobiera rozmiar obiektu.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Pobiera wartość obiektu jako serię kolejnych bajtów.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Ustawia wartość obiektu z kolejnych serię bajtów.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Ustawia wartość odwołanie do tego obiektu.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Pobiera kontekst pamięci, która reprezentuje adres wartość obiektu.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Tworzy kopię obiektu zarządzanego w przestrzeni adresowej aparatu debugowania.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Sprawdza, czy ten obiekt jest odwołanie o wartości null.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Porównuje obiekt do wskazanego.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Określa, czy ten obiekt tylko do odczytu.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Określa, czy obiekt przezroczystym serwerem proxy.|

## <a name="remarks"></a>Uwagi
 Ewaluator wyrażeń używa tego interfejsu jako klasę bazową do reprezentowania obiektów w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)