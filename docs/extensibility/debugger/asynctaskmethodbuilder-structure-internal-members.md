---
title: AsyncTaskMethodBuilder, struktura — składowe wewnętrzne | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2c6d3ecb3e23df4cb9c0d45a39765fd6c22fe013
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944551"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder, struktura — składowe wewnętrzne
W tym temacie opisano wewnętrznych członków <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> klasy. Aby uzyskać ogólne informacje dotyczące tej klasy, zobacz <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> temat referencyjny.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych składowych z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Składowe wewnętrzne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Właściwość ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Pobiera obiekt, który może być używany do jednoznacznego identyfikowania tego konstruktora do debugera.|  
|[pole m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Reprezentuje obiekt rodzajowy konstruktora, do której to wystąpienie nieogólnego deleguje odpowiednie uprawnienia.|  
  
## <a name="see-also"></a>Zobacz także  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)