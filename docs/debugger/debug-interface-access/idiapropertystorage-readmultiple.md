---
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742885"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Odczytuje określone właściwości z bieżącego zestawu właściwości.

## <a name="syntax"></a>Składnia

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>Parametry
 `cpspec`

podczas Liczba właściwości określona w tablicy `rgpspec`. Jeśli zero, metoda nie zwraca żadnych właściwości, ale zwraca `S_OK` jako kod sukcesu.

 `rgpspec`

podczas Tablica właściwości, które mają zostać odczytane. Właściwości można określić za pomocą identyfikatora właściwości lub opcjonalnej nazwy ciągu. Nie jest konieczne Określanie właściwości w określonej kolejności w tablicy. Tablica może zawierać zduplikowane właściwości, co powoduje duplikowanie wartości właściwości przy zwracaniu dla prostych właściwości. Nieproste właściwości powinny zwracać odmowę dostępu podczas próby otwarcia ich po raz drugi. Tablica może zawierać kombinację identyfikatorów właściwości i identyfikatorów ciągów. Ta tablica musi mieć co najmniej `cpspec` liczbę wartości właściwości.

 `rgvar`

[in. out] Tablica struktur `PROPVARIANT` (w przestrzeni nazw Microsoft. VisualStudio. OLE. Interop), które mają być wypełnione wartościami dla każdej właściwości. Tablica musi mieć co najmniej `cpspec` elementy. Obiekt wywołujący nie musi inicjować wartości w tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli nie odnaleziono co najmniej jednej właściwości. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli właściwość nie została znaleziona, odpowiadający jej wpis w tablicy `rgvar` zawiera `VARIANT` z typem `VT_EMPTY`.

## <a name="see-also"></a>Zobacz także
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)