---
description: Lista zadań podrzędnych zarejestrowanych w tym zadaniu.
title: m_children pola | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 311ab164551e46fbe1c30b5a6045a7993a900a67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901373"
---
# <a name="m_children-field"></a>m_children pola
Lista zadań podrzędnych zarejestrowanych w tym zadaniu.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego członka z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

## <a name="syntax"></a>Składnia

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Uwagi
 Gdy zadanie jest uruchomione, tylko wątek, który wykonuje zadanie, powinien uzyskać dostęp do tej tablicy.

 Jeśli zadanie zostanie ukończone, inne wątki będą mieć dostęp do tego pola, o ile nie dodają do niego niczego ani nie usuną niczego z niego.

## <a name="see-also"></a>Zobacz też
- [ContingentProperties, klasa](../../extensibility/debugger/contingentproperties-class-internal-members.md)
