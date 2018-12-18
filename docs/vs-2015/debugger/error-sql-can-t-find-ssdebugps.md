---
title: 'Błąd: SQL można&#39;możemy znaleźć SSDEBUGPS | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 47e0557e3ad2022250d54b7bd45844825ff79a03
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757468"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Błąd: SQL można&#39;możemy znaleźć SSDEBUGPS
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
    regsrv32 ssdebugps.dll  
    ```



