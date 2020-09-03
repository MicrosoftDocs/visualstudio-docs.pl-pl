---
title: IDebugDefaultPort2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732317"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Ten interfejs zapewnia kilka metod uzyskiwania dostępu do serwera i usług powiadamiania o porcie.

## <a name="syntax"></a>Składnia

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio implementuje ten interfejs, aby reprezentować port debugowania w celu uzyskania dostępu do programów. Dostawca portu niestandardowego może również zaimplementować ten interfejs, jeśli obsługuje debugowanie zdalne.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Argument metod w interfejsie [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) dostarcza ten interfejs. Wywołanie [polecenia QueryInterface](/cpp/atl/queryinterface) w interfejsie [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) może również uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod zdefiniowanych w [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Pobiera interfejs powiadomień portu z tego portu.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Pobiera interfejs do serwera obsługującego ten port.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Określa, czy ten port jest uruchomiony na komputerze lokalnym.|

## <a name="remarks"></a>Uwagi
 Nazwa " `IDebugDefaultPort2` " jest bitem elementu Misnomer, ponieważ nie reprezentuje domyślnego portu. Może być wywoływana "IDebugPort3".

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
