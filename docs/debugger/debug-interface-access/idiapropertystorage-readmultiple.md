---
title: IDiaPropertyStorage::ReadMultiple | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d30666aa986d7069ee3ad3bd8c9a0696cc5aaae6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645618"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Odczytuje określony właściwości z bieżącego zestawu właściwości.

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

[in] Liczba właściwości określonych w `rgpspec` tablicy. Jeśli zero, metoda zwraca żadnych właściwości, ale przywraca `S_OK` jako kod powodzenia.

 `rgpspec`

[in] Tablica właściwości do odczytu. Właściwości można określić Identyfikatora właściwości lub nazwa opcjonalny ciąg. Nie jest to konieczne określić właściwości w określonej kolejności w tablicy. Tablica może zawierać zduplikowanych właściwości, wynikiem wartości zduplikowaną właściwość przy powrocie z prostych właściwości. Inne niż proste właściwości powinien zwrócić odmowa dostępu w momencie próby otwierać je po raz drugi. Tablica może zawierać kombinację identyfikatory właściwości i identyfikatory ciągu. Ta tablica musi mieć co najmniej `cpspec` liczba wartości właściwości.

 `rgvar`
- [out w] Tablica `PROPVARIANT` struktury (w przestrzeni nazw Microsoft.VisualStudio.OLE.Interop) w celu wprowadzenia wartości dla każdej właściwości. Tablica musi wynosić co najmniej `cpspec` elementów w rozmiarze. Obiekt wywołujący nie musi zainicjować wartości w tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli jeden lub więcej właściwości nie został znaleziony. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli nie znaleziono właściwości, odpowiadający mu wpis w `rgvar` tablica zawiera `VARIANT` z typem `VT_EMPTY`.

## <a name="see-also"></a>Zobacz też
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)