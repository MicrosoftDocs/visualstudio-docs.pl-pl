---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722506"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Umożliwia aparatowi debugowania przesłonięcie domyślnego zachowania [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika po zakończeniu sesji debugowania.

## <a name="syntax"></a>Składnia

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez aparaty debugowania. Jest to przydatne w przypadku hostów, które mogą tworzyć i zniszczyć wiele programów w okresie istnienia procesu.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugProgramDestroyEventFlags2` .

|Metoda|Opis|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Pobiera flagi niszczenia programów.|

## <a name="remarks"></a>Uwagi
 Domyślnym zachowaniem [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika jest powrót do trybu projektowania po wysłaniu przez wszystkie programy zdarzenia zniszczenia programu. Ten interfejs umożliwia aparatowi debugowania zmianę tego zachowania.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
