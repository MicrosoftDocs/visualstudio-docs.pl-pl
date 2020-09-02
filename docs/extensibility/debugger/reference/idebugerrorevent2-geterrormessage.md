---
title: 'IDebugErrorEvent2:: GetErrorMessage | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730043"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Zwraca informacje, które umożliwiają konstruowanie komunikatu o błędzie z możliwością odczytu przez człowieka.

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
określoną Zwraca wartość z wyliczenia [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) opisującą typ komunikatu.

`pbstrErrorFormat`\
określoną Format komunikatu końcowego dla użytkownika (patrz "uwagi", aby uzyskać szczegółowe informacje).

`hrErrorReason`\
określoną Kod błędu dotyczący wiadomości.

`pdwType`\
określoną Ważność błędu (Użyj stałych MB_XXX `MessageBox` , na przykład, `MB_EXCLAMATION` lub `MB_WARNING` ).

`pbstrHelpFileName`\
określoną Ścieżka do pliku pomocy (w przypadku braku pliku pomocy należy ustawić wartość null).

`pdwHelpId`\
określoną Identyfikator tematu pomocy do wyświetlenia (Ustaw wartość 0, jeśli nie ma tematu pomocy).

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Komunikat o błędzie powinien być sformatowany wzdłuż wierszy `"What I was doing.  %1"` . `"%1"`Następnie zostanie on zastąpiony przez obiekt wywołujący z komunikatem o błędzie uzyskanym z kodu błędu (który jest zwracany w programie `hrErrorReason` ). `pMessageType`Parametr informuje obiekt wywołujący o sposobie wyświetlania końcowego komunikatu o błędzie.

## <a name="see-also"></a>Zobacz też
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
