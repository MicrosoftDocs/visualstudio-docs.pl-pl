---
title: AsyncTaskMethodBuilder&lt;TResult&gt; struktura — składowe wewnętrzne | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6dc0f1a2cf8be65d812591b6d0d87fef15b42cd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926161"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; struktura — składowe wewnętrzne
W tym temacie opisano wewnętrznych członków <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> klasy. Aby uzyskać ogólne informacje dotyczące tej klasy, zobacz <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> temat referencyjny.

 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Zestaw:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych składowych z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).

## <a name="syntax"></a>Składnia

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Składowe wewnętrzne

|Nazwa|Opis|
|----------|-----------------|
|[Właściwość ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Pobiera obiekt, który może być używany do jednoznacznego identyfikowania tego konstruktora do debugera.|
|[pole m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Reprezentuje opóźnieniem zainicjowane utworzone zadanie.|

## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)