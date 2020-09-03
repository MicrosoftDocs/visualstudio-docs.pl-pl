---
title: IDebugPointerObject3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8605f1cdd50b6e98d6e30a7b550cce1d22543ff9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725466"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Reprezentuje wskaźnik w drzewie analizy i rozszerza interfejs **IDebugPointerObject** .

## <a name="syntax"></a>Składnia

```
IDebugPointerObject3 : IDebugPointerObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń (EE) implementuje ten interfejs.

## <a name="methods"></a>Metody
 Oprócz metod interfejsu [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) , ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|Pobiera adres wskaźnika.|

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
