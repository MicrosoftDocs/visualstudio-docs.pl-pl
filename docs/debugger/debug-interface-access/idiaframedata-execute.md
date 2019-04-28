---
title: Idiaframedata::EXECUTE — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78440c703ece2aa54e54594d57156dbb17848915
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832668"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Wykonuje odwijanie stosu i zwraca wyniki w interfejsie ramki przeszukiwania stosu.

## <a name="syntax"></a>Składnia

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parametry
 `frame`

[in] [Idiastackwalkframe —](../../debugger/debug-interface-access/idiastackwalkframe.md) obiekt, który zawiera stan rejestrów ramki.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.

|Wartość|Opis|
|-----------|-----------------|
|E_DIA_INPROLOG|Nie można wykonać ramkę stosu w kodzie prologu.|
|E_DIA_SYNTAX|Błąd wystąpił w programie ramki analizy.|
|E_DIA_FRAME_ACCESS|Nie można rejestrów dostępu lub pamięci.|
|E_DIA_VALUE|Wystąpił błąd podczas obliczania wartości (na przykład, dzielenie przez zero).|

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana podczas debugowania do odkręcanie stosu. [Idiastackwalkframe —](../../debugger/debug-interface-access/idiastackwalkframe.md) obiektu jest implementowany przez aplikację klienta, aby otrzymywać aktualizacje w rejestrach i dostarcza metod używanych przez `execute` metody.

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)