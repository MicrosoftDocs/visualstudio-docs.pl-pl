---
description: W tym temacie opisano wewnętrzne składowe klasy System.Runtime.CompilerServices.AsyncVoidMethodBuilder.
title: Struktura AsyncVoidMethodBuilder — składowe wewnętrzne | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6606e26d14ba114ed8346c0cc11a81f8bdd3e8e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903636"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Struktura AsyncVoidMethodBuilder — składowe wewnętrzne
W tym temacie opisano wewnętrzne składowe <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> klasy. Ogólne informacje o tej klasie można znaleźć w <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> temacie referencyjnym.

 **Przestrzeń nazw:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Zestaw:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

## <a name="syntax"></a>Składnia

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Wewnętrzne elementy członkowskie

|Nazwa|Opis|
|----------|-----------------|
|[ObjectIdForDebugger, właściwość](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Pobiera obiekt, który może służyć do unikatowego identyfikowania tego konstruktora w debugerze.|
|[m_objectIdForDebugger pola](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Reprezentuje obiekt zainicjowany z lazily używany przez debuger do unikatowego identyfikowania tego konstruktora.|

## <a name="see-also"></a>Zobacz też
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Równoległe wewnętrzne rozszerzenia dla .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
