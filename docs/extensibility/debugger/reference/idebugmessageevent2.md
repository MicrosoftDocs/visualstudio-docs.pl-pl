---
title: IDebugMessageSavent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727362"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Ten interfejs jest używany przez aparat debugowania (DE) do wysyłania wiadomości do programu Visual Studio, która wymaga odpowiedzi od użytkownika.

## <a name="syntax"></a>Składnia

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 De implementuje ten interfejs, aby wysłać wiadomość do programu Visual Studio, który wymaga odpowiedzi użytkownika. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten interfejs. Moduł SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do `IDebugEvent2` interfejsu.

 Implementacja tego interfejsu musi komunikować wywołanie programu Visual Studio [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) do DE. Na przykład można to zrobić za pomocą wiadomości opublikowanej w wątku obsługi wiadomości DE lub obiekt implementujący ten interfejs może zawierać `IDebugMessageEvent2::SetResponse`odwołanie do DE i wywołać z powrotem do DE z odpowiedzią przekazywana do .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła ten obiekt zdarzenia, aby wyświetlić komunikat do użytkownika, który wymaga odpowiedzi. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) która jest dostarczana przez SDM, gdy jest dołączony do programu jest debugowany.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugMessageEvent2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Pobiera komunikat, który ma być wyświetlany.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Ustawia odpowiedź, jeśli istnieje, z okna komunikatu.|

## <a name="remarks"></a>Uwagi
 DE użyje tego interfejsu, jeśli wymaga określonej odpowiedzi od użytkownika dla określonej wiadomości. Na przykład jeśli DE pobiera komunikat "Odmowa dostępu" po próbie zdalnego dołączenia do programu, `IDebugMessageEvent2` DE wysyła ten `MB_RETRYCANCEL`konkretny komunikat do programu Visual Studio w przypadku o stylu okna komunikatu . Dzięki temu użytkownik może ponowić próbę lub anulować operację dołączania.

 DE określa, jak ten komunikat ma być obsługiwany przez następujące konwencje `MessageBox` funkcji Win32 (zobacz [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) szczegóły).

 Użyj interfejsu [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) do wysyłania wiadomości do programu Visual Studio, które nie wymagają odpowiedzi od użytkownika.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
