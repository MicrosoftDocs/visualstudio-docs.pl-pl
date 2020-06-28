---
title: 'IDiaPropertyStorage:: enum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89c5b6418e832dd145837e579cfded3f47022e00
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466603"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Pobiera moduł wyliczający dla właściwości w tym zestawie.

## <a name="syntax"></a>Składnia

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>Parametry
 `ppenum`

określoną Zwraca `IEnumSTATPROPSTG` obiekt (w przestrzeni nazw Microsoft. VisualStudio. OLE. Interop) reprezentujący Wyliczenie właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)