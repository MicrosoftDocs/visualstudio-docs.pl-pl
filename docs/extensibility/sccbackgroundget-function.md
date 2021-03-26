---
description: Ta funkcja pobiera z kontroli źródła każdego z określonych plików bez interakcji z użytkownikiem.
title: Funkcja SccBackgroundGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6d850b1f8493f3118cb4d3e49915361daa1e4837
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060461"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet, funkcja
Ta funkcja pobiera z kontroli źródła każdego z określonych plików bez interakcji z użytkownikiem.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parametry
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 nFiles

podczas Liczba plików określona w `lpFileNames` tablicy.

 lpFileNames

[in. out] Tablica nazw plików do pobrania.

> [!NOTE]
> Nazwy muszą być w pełni kwalifikowanymi nazwami plików lokalnych.

 flagiDW

podczas Flagi poleceń ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

podczas Unikatowa wartość skojarzona z tą operacją.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja została ukończona pomyślnie.|
|SCC_E_BACKGROUNDGETINPROGRESS|Trwa już pobieranie w tle (wtyczka do kontroli źródła powinna zwrócić tę wartość tylko wtedy, gdy nie obsługuje równoczesnych operacji wsadowych).|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest zawsze wywoływana na wątku innym niż ten, który załadował wtyczkę kontroli źródła. Ta funkcja nie powinna zostać zwrócona, dopóki nie zostanie ukończona; może jednak być wywoływana wielokrotnie z wieloma listami plików.

 Użycie `dwFlags` argumentu jest takie samo jak [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
