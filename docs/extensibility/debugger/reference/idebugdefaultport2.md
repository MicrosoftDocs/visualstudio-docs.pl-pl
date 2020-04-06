---
title: IDebugDefaultPort2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732317"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Ten interfejs zapewnia kilka metod uzyskiwania dostępu do serwera portu i obiektów powiadomień.

## <a name="syntax"></a>Składnia

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Visual Studio implementuje ten interfejs do reprezentowania portu debugowania dla uzyskiwania dostępu do programów. Dostawca portu niestandardowego można również zaimplementować ten interfejs, jeśli obsługuje zdalne debugowanie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Argument do metod w interfejsie [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) dostarcza tego interfejsu. Wywołanie [QueryInterface](/cpp/atl/queryinterface) na [interfejsie IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) można również uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod zdefiniowanych w [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)interfejs ten implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Pobiera interfejs powiadomień portu z tego portu.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Pobiera interfejs do serwera hostowania tego portu.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Określa, czy ten port jest uruchomiony na komputerze lokalnym.|

## <a name="remarks"></a>Uwagi
 Nazwa "`IDebugDefaultPort2`" jest trochę mylące, ponieważ nie reprezentuje domyślnego portu. Można go nazwać "IDebugPort3".

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
