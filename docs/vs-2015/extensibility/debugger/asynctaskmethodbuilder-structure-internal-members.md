---
title: Struktura AsyncTaskMethodBuilder — wewnętrzne elementy członkowskie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bfe640654c9de7daac9096aa4d75f5492a8a278
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555915"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder, struktura — składowe wewnętrzne
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym temacie opisano wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> klasy. Aby uzyskać ogólne informacje na temat tej klasy, zobacz temat informacje o <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> odwołaniach.  
  
 **Przestrzeń nazw:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, następująca składnia jest udostępniana w typowym języku pośrednim (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Wewnętrzne elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Właściwość ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Pobiera obiekt, który może być używany do jednoznacznego identyfikowania tego konstruktora w debugerze.|  
|[pole m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Reprezentuje obiekt konstruktora generycznego, do którego to wystąpienie nieogólne.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
