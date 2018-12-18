---
title: Pole m_children | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f044c2dae278a0656f1f9e4c41a3940d87658a64
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731040"
---
# <a name="mchildren-field"></a>m_children, pole
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lista zadań podrzędnych, które zostały zarejestrowane przy użyciu tego zadania.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Uwagi  
 Po uruchomieniu zadania tylko wątku, który wykonuje zadania powinien uzyskać dostęp do tej tablicy.  
  
 Jeśli zadanie zostało ukończone, inne wątki można uzyskać dostęp do tego pola tak długo, jak nie nic dodawać do niego ani nie usuwaj niczego, co z nich.  
  
## <a name="see-also"></a>Zobacz też  
 [ContingentProperties, klasa](../../extensibility/debugger/contingentproperties-class-internal-members.md)

