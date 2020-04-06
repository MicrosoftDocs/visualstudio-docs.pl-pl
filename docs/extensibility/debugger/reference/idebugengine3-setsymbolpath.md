---
title: IDebugEngine3::SetSymbolPath | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730659"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Ustawia ścieżkę lub ścieżki, które są wyszukiwane pod kątem symboli debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>Parametry

`szSymbolSearchPath`\
[w] Ciąg zawierający ścieżkę wyszukiwania symboli lub ścieżki. Szczegółowe informacje można znaleźć w "Uwagach". Nie może mieć wartości null.

`szSymbolCachePath`\
[w] Ciąg zawierający ścieżkę lokalną, w której można buforować symbole. Nie może mieć wartości null.

`Flags`\
[w] Nie używane; zawsze ustawiona na 0.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ciąg `szSymbolSearchPath` jest listą jednej lub więcej ścieżek, oddzielonych średnikami, do wyszukiwania symboli. Ścieżki te mogą być ścieżką lokalną, ścieżką w stylu UNC lub adresem URL. Ścieżki te mogą być również mieszanką różnych typów. Jeśli ścieżka jest UNC (na przykład \Symserver\Symbole), aparat debugowania powinien określić, \\czy ścieżka jest do serwera symboli i powinien być `szSymbolCachePath`w stanie załadować symbole z tego serwera, buforując je w ścieżce określonej przez .

 Ścieżka symbolu może również zawierać jedną lub więcej lokalizacji pamięci podręcznej. Pamięci podręczne są wyświetlane w kolejności priorytetu, z pamięci podręcznej o najwyższym priorytecie pierwszy i oddzielone symbolami *. Przykład:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 [Metoda LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) wykonuje rzeczywiste obciążenie symboli.

## <a name="see-also"></a>Zobacz też
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
