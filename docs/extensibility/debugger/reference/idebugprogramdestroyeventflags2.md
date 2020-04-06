---
title: IDebugProgramDestroyEventFlags2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722506"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Włącza aparat debugowania, aby zastąpić domyślne zachowanie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika po zakończeniu sesji debugowania.

## <a name="syntax"></a>Składnia

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez aparaty debugowania. Jest to przydatne dla hostów, które mogą tworzyć i niszczyć wiele programów w okresie istnienia procesu.

## <a name="methods"></a>Metody
 W poniższej tabeli `IDebugProgramDestroyEventFlags2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Pobiera program zniszczyć flagi.|

## <a name="remarks"></a>Uwagi
 Domyślnym zachowaniem [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika jest powrót do trybu projektowania po wysłaniu przez wszystkie programy zdarzenia zniszczenia programu. Ten interfejs umożliwia aparat debugowania, aby zmienić to zachowanie.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
