---
description: W tym artykule opisano wewnętrzne składowe klasy System.Runtime.CompilerServices.AsyncTaskMethodBuilder.
title: AsyncTaskMethodBuilder, struktura — składowe wewnętrzne
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5b21045688fc2be555c7a42d6e3b9014b66c761
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903843"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder, struktura — składowe wewnętrzne
W tym temacie opisano wewnętrzne składowe <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> klasy. Ogólne informacje o tej klasie można znaleźć w <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> temacie referencyjnym.

 **Przestrzeń nazw:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Zestaw:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

## <a name="syntax"></a>Składnia

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Wewnętrzne elementy członkowskie

|Nazwa|Opis|
|----------|-----------------|
|[ObjectIdForDebugger, właściwość](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Pobiera obiekt, który może służyć do unikatowego identyfikowania tego konstruktora w debugerze.|
|[m_builder pola](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Reprezentuje obiekt konstruktora ogólnego, do którego delegowane jest to wystąpienie inne niż ogólne.|

## <a name="see-also"></a>Zobacz też
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Równoległe wewnętrzne rozszerzenia dla .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
