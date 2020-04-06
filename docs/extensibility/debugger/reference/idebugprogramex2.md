---
title: IDebugProgramEx2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722327"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Ten interfejs umożliwia menedżerowi debugowania sesji (SDM) dołączenie do programu i uzyskanie węzła programu skojarzonego z programem.

## <a name="syntax"></a>Składnia

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca portu niestandardowego implementuje ten interfejs na tym samym obiekcie co interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) w celu umożliwienia SDM dołączyć do programu, jednocześnie umożliwiając dostawcy portu śledzenie wszystkich sesji dołączonych do programu. Dostawca portu niestandardowego można zaimplementować ten interfejs, jeśli wybierze.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 SDM wywołuje [QueryInterface](/cpp/atl/queryinterface) `IDebugProgram2` na interfejsie, aby uzyskać ten interfejs do śledzenia sesji, które zostały dołączone do programów.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugProgramEx2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dołącz](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Dołącza program do sesji.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Pobiera węzeł programu skojarzony z programem.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest prywatny między modułem SDM a programem.

## <a name="requirements"></a>Wymagania
 Nagłówek: Portpriv.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
