---
title: 'Błąd: Można SQL&#39;możemy znaleźć SSDEBUGPS | Dokumentacja firmy Microsoft'
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
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92e09a3dd2d1d70bd2e585e2de6b0fd1cca812b0
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154387"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Błąd: Można SQL&#39;możemy znaleźć SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Biblioteka SSDEBUGPS.dll to składnik Host debugowania programu SQL Server.  
  
 Ten błąd występuje, gdy chcesz rozpocząć debugowanie i wskazuje, że określony plik nie jest obecny na [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] maszyny. Możliwe przyczyny to nigdy nie uruchomiono albo ustawienia zdalne debugowanie lub że jakiś sposób ten plik został usunięty.  
  
 Istnieją dwa sposoby, aby rozwiązać ten problem: ponownie instalację zdalnego debugowania i przez skopiowanie pliku do [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] maszyny.  
  
 Ponowne uruchamianie konfiguracji zdalnego debugowania, postępuj zgodnie z instrukcjami w artykule [zdalne debugowanie](../debugger/remote-debugging.md).  
  
 Jeśli można znaleźć kopię Biblioteka ssdebugps.dll, możesz skopiować go na [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] maszyny. Jeśli jest obecny, plik zostanie w \Program Files\ katalogu wspólnego Files\Microsoft Shared\SQL debugowania. Może okazać się na innym [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] komputerze lub na komputerze, na którym [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] zainstalowane.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Aby skopiować Biblioteka SSDEBUGPS.dll na komputerze programu SQL Server 2005  
  
1.  Skopiuj plik do katalogu z taką samą nazwę i ścieżkę na [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] maszyny.  
  
2.  Zarejestruj go, otwierając **polecenia**, a następnie uruchamiając następujące polecenie:  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```



