---
title: 'Błąd: użytkownik nie może wykonać procedury składowanej sp_enable_sql_debug | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 759386728283d3d39219133e53668afe3259714a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697671"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Błąd: użytkownik nie mógł wykonać procedury przechowywanej sp_enable_sql_debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nie można wykonać procedury składowanej sp_enable_sql_debug na serwerze. Może to być spowodowane przez:  
  
- Problem z połączeniem. Musisz mieć stabilne połączenie z serwerem.  
  
- Brak wymaganych uprawnień na serwerze. Aby debugować na SQL Server 2005, zarówno konto z programem Visual Studio, jak i konto używane do nawiązywania połączenia z SQL Server muszą być członkami roli sysadmin. Konto używane do nawiązywania połączenia z SQL Server jest kontem użytkownika systemu Windows (Jeśli używasz uwierzytelniania systemu Windows) lub kontem z IDENTYFIKATORem użytkownika i hasłem (Jeśli używasz uwierzytelniania SQL).  
  
  Aby uzyskać więcej informacji, zobacz [How to: Set SQL Server Permissions for debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Ustawianie uprawnień SQL Server na potrzeby debugowania](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Konfigurowanie debugowania SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)
