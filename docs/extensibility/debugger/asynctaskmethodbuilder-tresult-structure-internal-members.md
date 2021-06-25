---
description: W tym temacie opisano wewnętrzne składowe klasy System.Runtime.CompilerServices.AsyncTaskMethodBuilder.
title: AsyncTaskMethodBuilder, &lt; struktura TResult &gt; — składowe wewnętrzne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca9d5ccfcd5870902cc40a623aabb93a3115f469
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903804"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>Struktura TResult AsyncTaskMethodBuilder &lt; &gt; — składowe wewnętrzne
W tym temacie opisano wewnętrzne składowe <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> klasy. Ogólne informacje o tej klasie można znaleźć w <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> temacie referencyjnym.

 **Przestrzeń nazw:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Zestaw:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

## <a name="syntax"></a>Składnia

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Wewnętrzne elementy członkowskie

|Nazwa|Opis|
|----------|-----------------|
|[ObjectIdForDebugger, właściwość](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Pobiera obiekt, który może służyć do unikatowego identyfikowania tego konstruktora w debugerze.|
|[m_task pola](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Reprezentuje zainicjowane z lazily wbudowane zadanie.|

## <a name="see-also"></a>Zobacz też
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Równoległe wewnętrzne rozszerzenia dla .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
