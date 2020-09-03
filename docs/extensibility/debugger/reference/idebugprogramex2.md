---
title: IDebugProgramEx2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722327"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Ten interfejs umożliwia dołączenie Menedżera debugowania sesji (SDM) do programu i uzyskanie węzła programu skojarzonego z programem.

## <a name="syntax"></a>Składnia

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Niestandardowy dostawca portu implementuje ten interfejs na tym samym obiekcie co Interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , aby umożliwić dołączenie modelu SDM do programu w tym samym czasie, co pozwala dostawcy portów śledzić wszystkie sesje dołączone do programu. Dostawca portu niestandardowego może zaimplementować ten interfejs, jeśli zostanie wybrany.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Model SDM wywołuje [QueryInterface](/cpp/atl/queryinterface) w `IDebugProgram2` interfejsie, aby uzyskać ten interfejs do śledzenia sesji dołączonych do programów.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugProgramEx2` .

|Metoda|Opis|
|------------|-----------------|
|[Dołącz](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Dołącza program do sesji.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Pobiera węzeł programu skojarzony z programem.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest prywatny między modelem SDM a programem.

## <a name="requirements"></a>Wymagania
 Nagłówek: Portpriv. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
