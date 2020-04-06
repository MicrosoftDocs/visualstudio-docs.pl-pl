---
title: pole m_children | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738425"
---
# <a name="m_children-field"></a>Pole m_children
Lista zadań podrzędnych zarejestrowanych w tym zadaniu.

 **Obszar nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaż:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z programu .NET Framework, następująca składnia znajduje się we wspólnym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Uwagi
 Gdy zadanie jest uruchomione, tylko wątek, który wykonuje zadanie należy uzyskać dostęp do tej tablicy.

 Jeśli zadanie zostało ukończone, inne wątki mogą uzyskać dostęp do tego pola, o ile nie dodają do niego niczego ani nie usuwają niczego z niego.

## <a name="see-also"></a>Zobacz też
- [Klasa Właściwości warunkowe](../../extensibility/debugger/contingentproperties-class-internal-members.md)
