---
title: 'Błąd: Użytkownik może nie wykonać procedury przechowywanej sp_enable_sql_debug | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 1f463aca03cd0e869f4028f8e086c623295fd2f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799399"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Błąd: Użytkownik może nie wykonać procedury przechowywanej sp_enable_sql_debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Procedury przechowywanej sp_enable_sql_debug nie można wykonać na serwerze. Może to być spowodowane:  
  
- Problem z połączeniem. Musisz mieć stabilne połączenie z serwerem.  
  
- Brak wystarczających uprawnień na serwerze. Do debugowania w programie SQL Server 2005, zarówno w przypadku konta, programem Visual Studio, jak i konto używane do łączenia się z serwerem SQL muszą być członkami roli sysadmin. Konto używane do łączenia się z serwerem SQL jest kontem użytkownika Windows (Jeśli używasz uwierzytelniania Windows) lub konto z Identyfikatorem użytkownika i hasło (Jeśli używasz uwierzytelniania SQL).  
  
  Aby uzyskać więcej informacji, zobacz [jak: Ustawianie uprawnień programu SQL Server do debugowania](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Ustawianie uprawnień programu SQL Server do debugowania](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Konfigurowanie debugowania SQL](http://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)
