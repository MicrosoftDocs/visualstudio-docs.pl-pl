---
description: Lista zadań podrzędnych, które są zarejestrowane w tym zadaniu.
title: m_children pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5aaf29d76a7bbd81a416c86360f315bc5c09b76c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158872"
---
# <a name="m_children-field"></a>pole m_children
Lista zadań podrzędnych, które są zarejestrowane w tym zadaniu.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Uwagi
 Gdy zadanie jest uruchomione, tylko wątek, który wykonuje zadanie, powinien uzyskać dostęp do tej tablicy.

 Jeśli zadanie zostanie ukończone, inne wątki mogą uzyskać dostęp do tego pola, o ile nie dodają do niego niczego lub usuwają coś z niego.

## <a name="see-also"></a>Zobacz też
- [Klasa ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
