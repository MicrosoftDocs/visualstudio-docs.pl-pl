---
title: Klasa ContingentProperties — Wewnętrzne elementy członkowskie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3f332c715c8a182b30191cd96c8f1d1438cbdefd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930489"
---
# <a name="contingentproperties-class---internal-members"></a>Klasa ContingentProperties — Wewnętrzne elementy członkowskie
Zawiera dodatkowe właściwości dla <xref:System.Threading.Tasks.Task> obiektu.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, następująca składnia jest udostępniana w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Elementy członkowskie

### <a name="fields"></a>Pola

|Nazwa|Opis|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Lista zadań podrzędnych, które są zarejestrowane w tym zadaniu.|

## <a name="remarks"></a>Uwagi
 .NET Framework inicjuje pola tej klasy tylko wtedy, gdy są one zbędne.

## <a name="see-also"></a>Zobacz też
- [Wewnętrzne rozszerzenia równoległe dla .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
