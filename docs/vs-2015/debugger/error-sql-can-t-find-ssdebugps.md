---
title: 'Błąd: SQL może&#39;t Find SSDEBUGPS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 25462a99bd3e773f03af3918a9e25d11ed006c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185214"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Błąd: SQL może&#39;t Find SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll to składnik hosta debugowania SQL Server.  
  
 Ten błąd występuje podczas próby uruchomienia debugowania i wskazuje, że określony plik nie jest obecny na [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] maszynie. Możliwe przyczyny to, że Instalator zdalnego debugowania nigdy nie został uruchomiony lub właśnie ten plik został usunięty.  
  
 Istnieją dwa sposoby rozwiązania tego błędu: przez odinstalowanie Instalatora zdalnego debugowania i skopiowanie pliku na [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] komputer.  
  
 Aby ponownie uruchomić Instalatora zdalnego debugowania, postępuj zgodnie z instrukcjami na stronie [debugowanie zdalne](../debugger/remote-debugging.md).  
  
 Jeśli można znaleźć kopię ssdebugps.dll, można skopiować ją na [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] maszynę. Jeśli jest obecny, plik będzie w katalogu \Program Files \ Common Files\Microsoft Shared\SQL Debug. Można go znaleźć na innym [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] komputerze lub na komputerze, na którym [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] zainstalowano program.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Aby skopiować SSDEBUGPS.dll na maszynę SQL Server 2005  
  
1. Skopiuj plik do katalogu o tej samej nazwie i ścieżce na [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] komputerze.  
  
2. Zarejestruj go, otwierając **wiersz polecenia**i uruchamiając następujące polecenie:  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```
