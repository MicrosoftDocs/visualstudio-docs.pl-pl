---
title: 'Błąd: Wykonanie Transact-SQL zakończyło się bez debugowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b67900f02a81a6a28279268c3fe6fa067bcdaedc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787643"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Błąd: Wykonanie Transact-SQL zakończyło się bez debugowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd występuje podczas próby debugowania języka Transact-SQL lub procedury SQLCLR i debuger nie odbiera komunikaty debugowania z programu SQL Server.  
  
 Może to być ze względu na problemy z siecią lub problemy w programie SQL Server, ale najbardziej prawdopodobną przyczyną jest problem z uprawnieniami.  
  
 Zaangażowanych dwa konta:  
  
- Konto aplikacji znajduje się konto użytkownika, który [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] działa jako.  
  
- Konto połączenia jest to tożsamość używana do nawiązywania połączeń z programem SQL Server. To nie jest zawsze taki sam jak tożsamość, która Visual Studio działa tak, jakby połączenie za pomocą uwierzytelniania SQL.  
  
  Debugowanie SQL wymaga, aby konto aplikacji musi odpowiadać kontu połączenia lub być sysadmin.  
  
  Jeśli używasz identyfikatora logowania SQL, takich jak Ameryka Południowa konta aplikacji musi być Instalatora na serwerze SQL, administrator systemu. Domyślnie administratorzy na komputerze program SQL server jest uruchomiony są głównym programu SQL Server.  
  
  Aby naprawić ten błąd, konieczne może być:  
  
- Sprawdź ustawienia uprawnień. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie uprawnień programu SQL Server dla debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Upewnij się, że debugowanie SQL, jeśli skonfigurowane prawidłowo.  
  
- Zapoznaj się z administratorem sieci lub bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie debugowania SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Porady: Ustawianie uprawnień programu SQL Server do debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)



