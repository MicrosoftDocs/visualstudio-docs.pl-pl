---
title: IDiaPropertyStorage::ReadMultiple | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c36dcd5fc0f6e02804c57d94c9ae1d5c05e3b19f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796236"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Odczytuje określony właściwości z bieżącego zestawu właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [out w] Tablica `PROPVARIANT` struktury (w przestrzeni nazw Microsoft.VisualStudio.OLE.Interop) w celu wprowadzenia wartości dla każdej właściwości. Tablica musi wynosić co najmniej `cpspec` elementów w rozmiarze. Obiekt wywołujący nie musi zainicjować wartości w tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli jeden lub więcej właściwości nie został znaleziony. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie znaleziono właściwości, odpowiadający mu wpis w `rgvar` tablica zawiera `VARIANT` z typem `VT_EMPTY`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



