---
title: Klasa właściwości warunkowych - Członkowie wewnętrzni | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6441cafcc34a06464061b41691ea5faa32fc359
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739101"
---
# <a name="contingentproperties-class---internal-members"></a>Klasa Właściwości warunkowe — elementy wewnętrzne
Zawiera dodatkowe właściwości <xref:System.Threading.Tasks.Task> obiektu.

 **Obszar nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaż:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z programu .NET Framework, następująca składnia znajduje się we wspólnym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Elementy członkowskie

### <a name="fields"></a>Pola

|Nazwa|Opis|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Lista zadań podrzędnych zarejestrowanych w tym zadaniu.|

## <a name="remarks"></a>Uwagi
 Program .NET Framework inicjuje pola tej klasy tylko wtedy, gdy są one potrzebne.

## <a name="see-also"></a>Zobacz też
- [Wewnętrzne rozszerzenia równoległego dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
