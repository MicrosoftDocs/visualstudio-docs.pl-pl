---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e646a248e4b7da03a9dbad9bcea2470d9d0f450
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876013"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Ten interfejs zapewnia kilka metod uzyskania dostępu do portów serwera i powiadomienie urządzenia.

## <a name="syntax"></a>Składnia

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio implementuje ten interfejs do reprezentowania port debugowania, aby uzyskać dostęp do programów. Dostawca numery portów mogą także implementować ten interfejs, jeśli obsługuje, zdalne debugowanie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Argument do metody [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfejs dostarcza ten interfejs. Wywoływanie [QueryInterface](/cpp/atl/queryinterface) na [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsu można również uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metody zdefiniowane w [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Pobiera interfejs powiadamiania portu z tego portu.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Pobiera interfejs do serwera obsługującego ten port.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Określa, czy ten port jest uruchomiony na komputerze lokalnym.|

## <a name="remarks"></a>Uwagi
 Nazwa "`IDebugDefaultPort2`" jest nieco misnomer, ponieważ nie reprezentuje domyślny port. Może być wywoływana "IDebugPort3."

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)