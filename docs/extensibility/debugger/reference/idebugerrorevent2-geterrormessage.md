---
title: IDebugErrorEvent2::GetErrorMessage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730043"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Zwraca informacje, które umożliwiają budowę komunikatu o błędzie czytelnym dla człowieka.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Parametry
`pMessageType`\
[na zewnątrz] Zwraca wartość z wyliczenia [MESSAGETYPE,](../../../extensibility/debugger/reference/messagetype.md) opisując typ wiadomości.

`pbstrErrorFormat`\
[na zewnątrz] Format ostatniej wiadomości do użytkownika (szczegółowe informacje znajdują się w części "Uwagi").

`hrErrorReason`\
[na zewnątrz] Kod błędu, o który chodzi w komunikacie.

`pdwType`\
[na zewnątrz] Ważność błędu (użyj MB_XXX stałych ; na `MessageBox`przykład lub `MB_EXCLAMATION` `MB_WARNING`).

`pbstrHelpFileName`\
[na zewnątrz] Ścieżka do pliku pomocy (ustawiona na wartość null, jeśli nie ma pliku pomocy).

`pdwHelpId`\
[na zewnątrz] Identyfikator tematu pomocy do wyświetlenia (ustawiona na 0, jeśli nie ma tematu pomocy).

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Komunikat o błędzie powinien być sformatowany zgodnie z poleceniem `"What I was doing.  %1"`. Następnie `"%1"` zostanie zastąpiony przez wywołującego z komunikatem o błędzie pochodzącym z `hrErrorReason`kodu błędu (który jest zwracany w ). Parametr `pMessageType` informuje wywołującego, jak powinien być wyświetlany końcowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
