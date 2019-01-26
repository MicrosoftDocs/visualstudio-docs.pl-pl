---
title: ContingentProperties, klasa — składowe wewnętrzne | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26f672a9d18e4963dba47b46a12e113e0a25a618
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001553"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties, klasa — składowe wewnętrzne
Zawiera dodatkowe właściwości <xref:System.Threading.Tasks.Task> obiektu.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych składowych z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="fields"></a>Pola  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|Lista zadań podrzędnych, które zostały zarejestrowane przy użyciu tego zadania.|  
  
## <a name="remarks"></a>Uwagi  
 .NET Framework inicjuje pól tej klasy, tylko wtedy, gdy są potrzebne.  
  
## <a name="see-also"></a>Zobacz także  
 [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)