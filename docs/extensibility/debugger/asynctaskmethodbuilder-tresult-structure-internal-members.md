---
title: AsyncTaskMethodBuilder&lt;TResult&gt; Structure - Elementy wewnętrzne | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c4f4da7070af09937af9e047ec83142584942e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739337"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;Struktura&gt; TResult - elementy wewnętrzne
W tym temacie opisano <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> wewnętrznych członków klasy. Aby uzyskać ogólne informacje na <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> temat tej klasy, zobacz temat odwołania.

 **Obszar nazw:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Montaż:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z programu .NET Framework, następująca składnia znajduje się we wspólnym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Członkowie wewnętrzni

|Nazwa|Opis|
|----------|-----------------|
|[Właściwość ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Pobiera obiekt, który może służyć do jednoznacznej identyfikacji tego konstruktora do debugera.|
|[Pole m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Reprezentuje leniwie zainicjowane zadanie zbudowane.|

## <a name="see-also"></a>Zobacz też
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Wewnętrzne rozszerzenia równoległego dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
