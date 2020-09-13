---
title: AsyncTaskMethodBuilder, struktura — składowe wewnętrzne
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f79ee4c717774ef61fc0aa07fe7ecf2c5c216c04
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036889"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Struktura AsyncTaskMethodBuilder — wewnętrzne elementy członkowskie
W tym temacie opisano wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> klasy. Aby uzyskać ogólne informacje na temat tej klasy, zobacz temat informacje o <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> odwołaniach.

 **Przestrzeń nazw:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Zestaw:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, następująca składnia jest udostępniana w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Wewnętrzne elementy członkowskie

|Nazwa|Opis|
|----------|-----------------|
|[Właściwość ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Pobiera obiekt, który może być używany do jednoznacznego identyfikowania tego konstruktora w debugerze.|
|[pole m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Reprezentuje obiekt konstruktora generycznego, do którego to wystąpienie nieogólne.|

## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Wewnętrzne rozszerzenia równoległe dla .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
