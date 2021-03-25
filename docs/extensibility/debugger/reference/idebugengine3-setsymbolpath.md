---
description: Ustawia ścieżkę lub ścieżki przeszukiwane pod kątem symboli debugowania.
title: 'IDebugEngine3:: SetSymbolPath | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3bc24aa6ae07505f4f1fce16593f11e44e752a9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066124"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Ustawia ścieżkę lub ścieżki przeszukiwane pod kątem symboli debugowania.

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
podczas Ciąg zawierający ścieżkę wyszukiwania symboli lub ścieżki. Aby uzyskać szczegółowe informacje, zobacz "uwagi". Nie może mieć wartości null.

`szSymbolCachePath`\
podczas Ciąg zawierający ścieżkę lokalną, w której symbole mogą być buforowane. Nie może mieć wartości null.

`Flags`\
podczas Nieużywane; zawsze ustawione na 0.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ten ciąg `szSymbolSearchPath` jest listą co najmniej jednej ścieżki rozdzieloną średnikami, aby wyszukać symbole. Ścieżki te mogą być ścieżką lokalną, ścieżką w stylu UNC lub adresem URL. Te ścieżki mogą być również kombinacją różnych typów. Jeśli ścieżka jest ścieżką UNC (na przykład \\ \Symserver\Symbols), aparat debugowania powinien określić, czy ścieżka należy do serwera symboli, i powinno być możliwe załadowanie symboli z tego serwera, buforowanie ich w ścieżce określonej przez `szSymbolCachePath` .

 Ścieżka symboli może również zawierać jedną lub więcej lokalizacji pamięci podręcznej. Pamięć podręczna jest wyświetlana w kolejności priorytetu, z najwyższym priorytetem pamięci podręcznej i oddzielona przez * symbole. Na przykład:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Metoda [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) wykonuje rzeczywiste obciążenie symboli.

## <a name="see-also"></a>Zobacz też
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
