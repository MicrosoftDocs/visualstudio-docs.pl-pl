---
title: ContingentProperties, klasa — składowe wewnętrzne | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f6778aef90361a7751ccd744fcf93822f8f97db
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757278"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties, klasa — składowe wewnętrzne
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zawiera dodatkowe właściwości <xref:System.Threading.Tasks.Task> obiektu.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych składowych z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
