---
title: IDebugErrorEvent2::GetErrorMessage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95b94dca9ef948a07b5c6458a9c8c53c8612eddd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920165"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Zwraca informacje, które umożliwiają konstrukcji czytelny dla człowieka komunikat.

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

#### <a name="parameters"></a>Parametry
 `pMessageType`

 [out] Zwraca wartość z zakresu od [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) wyliczenie, opisujące typ komunikatu.

 `pbstrErrorFormat`

 [out] Format komunikatu końcowego użytkownika (zobacz "Uwagi", aby uzyskać szczegółowe informacje).

 `hrErrorReason`

 [out] Kod błędu: komunikat dotyczy.

 `pdwType`

 [out] Ważność błędu (Użyj stałych MB_XXX dla `MessageBox`, na przykład `MB_EXCLAMATION` lub `MB_WARNING`).

 `pbstrHelpFileName`

 [out] Ścieżka do pliku pomocy (zestaw ma wartość null, jeśli nie ma żadnego pliku pomocy).

 `pdwHelpId`

 [out] Identyfikator tematu pomocy do wyświetlenia (wartość 0, jeśli Brak tematu pomocy).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Komunikat o błędzie powinien mieć format wzdłuż linii `"What I was doing.  %1"`. `"%1"` Będą następnie zastąpione przez obiekt wywołujący komunikat o błędzie, pochodzące z kodu błędu (który jest zwracany w `hrErrorReason`). `pMessageType` Parametr informuje obiekt wywołujący jak ostatni komunikat o błędzie powinien być wyświetlany.

## <a name="see-also"></a>Zobacz też
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)