---
description: Odczytuje określone właściwości z bieżącego zestawu właściwości.
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c7d0191d17074ec41b5fc73b3e33ba94b845a96e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148151"
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

podczas Liczba właściwości określonych w `rgpspec` tablicy. Jeśli zero, metoda nie zwraca żadnych właściwości, ale zwraca `S_OK` jako kod sukcesu.

 `rgpspec`

podczas Tablica właściwości, które mają zostać odczytane. Właściwości można określić za pomocą identyfikatora właściwości lub opcjonalnej nazwy ciągu. Nie jest konieczne Określanie właściwości w określonej kolejności w tablicy. Tablica może zawierać zduplikowane właściwości, co powoduje duplikowanie wartości właściwości przy zwracaniu dla prostych właściwości. Nieproste właściwości powinny zwracać odmowę dostępu podczas próby otwarcia ich po raz drugi. Tablica może zawierać kombinację identyfikatorów właściwości i identyfikatorów ciągów. Ta tablica musi mieć co najmniej `cpspec` liczbę wartości właściwości.

 `rgvar`

[in. out] Tablica `PROPVARIANT` struktur (w przestrzeni nazw Microsoft. VisualStudio. OLE. Interop), która ma zostać wypełniona wartościami dla każdej właściwości. Tablica musi mieć co najmniej `cpspec` elementy. Obiekt wywołujący nie musi inicjować wartości w tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie znaleziono co najmniej jednej właściwości. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli właściwość nie została znaleziona, odpowiadający jej wpis w `rgvar` tablicy zawiera `VARIANT` Typ `VT_EMPTY` .

## <a name="see-also"></a>Zobacz też
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
