---
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4012b919cffc5e16433567fac283ac731d4d215c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353280"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Reprezentuje wartość wyliczenia typu podstawowego z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu.

## <a name="syntax"></a>Składnia

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Metody
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Pobiera typ pierwotny, powiązanych z tym polem.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll