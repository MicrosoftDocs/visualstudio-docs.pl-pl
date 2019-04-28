---
title: IDebugEngine3::SetSymbolPath | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3799043b82a4e0d0993e7de255f69592c6b89534
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875279"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Ustawia ścieżki lub ścieżek, które są przeszukiwane pod kątem symboli debugowania.

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

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`szSymbolSearchPath`|[in] Ciąg zawierający ścieżkę wyszukiwania symbolu lub ścieżki. Aby uzyskać szczegółowe informacje, zobacz "Uwagi". Nie może mieć wartości null.|
|`szSymbolCachePath`|[in] Ciąg zawierający ścieżkę lokalną, gdzie symbole mogą być buforowane. Nie może mieć wartości null.|
|`Flags`|[in] Nie jest używany; zawsze ustawiony na 0.|

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ciąg `szSymbolSearchPath` znajduje się lista jedną lub więcej ścieżek, oddzielając je średnikami do wyszukiwania symboli. Tych ścieżek może być ścieżką lokalną, ścieżka UNC stylu lub adresu URL. Te ścieżki mogą być także kombinacji różnych typów. Jeśli ścieżka UNC (na przykład \\\Symserver\Symbols), a następnie aparat debugowania należy ustalić, czy ścieżka do serwera symboli i powinno być możliwe załadować symbole z tego serwera, buforowanie ich w ścieżce określonej przez `szSymbolCachePath`.

 Ścieżka symboli może również zawierać jedną lub więcej lokalizacji pamięci podręcznej. Pamięci podręczne są wymienione jako pierwsze w kolejności priorytetów z najwyższy priorytet pamięci podręcznej i oddzielone * symboli. Na przykład:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com
```

 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) metoda przeprowadza rzeczywiste obciążenie symboli.

## <a name="see-also"></a>Zobacz też
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)