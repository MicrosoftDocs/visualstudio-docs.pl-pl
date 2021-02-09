---
title: 'IDebugCoreServer3:: QueryIsLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad3b442382f26c1754689c005793c489b9cd5d3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923179"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
Określa, czy serwer jest lokalnym obiektem wywołującym.

## <a name="syntax"></a>Składnia

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Wartość zwracana
 Zwraca wartość `S_OK` wskazującą, że serwer jest lokalny. Zwraca `S_FALSE` czy serwer działa z wystąpienia msvsmon.exe, które jest zwykle używane do zdalnego debugowania.

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
