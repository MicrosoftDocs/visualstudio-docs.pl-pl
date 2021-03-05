---
description: Ten interfejs umożliwia dołączenie Menedżera debugowania sesji (SDM) do programu i uzyskanie węzła programu skojarzonego z programem.
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3efe419eaf037602ce1148c898c6c30dd86d23b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149577"
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
