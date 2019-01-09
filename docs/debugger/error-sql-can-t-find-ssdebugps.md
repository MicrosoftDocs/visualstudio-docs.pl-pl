---
title: 'Błąd: Można SQL&#39;możemy znaleźć SSDEBUGPS | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0c10c2ba2a5b9da700d698d553cdf49a7a0a136
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54153670"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Błąd: Można SQL&#39;możemy znaleźć SSDEBUGPS

Biblioteka SSDEBUGPS.dll to składnik Host debugowania programu SQL Server.

Ten błąd występuje, gdy chcesz rozpocząć debugowanie i wskazuje, że określony plik nie jest obecny na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszyny. Możliwe przyczyny to nigdy nie uruchomiono albo ustawienia zdalne debugowanie lub że jakiś sposób ten plik został usunięty.

Istnieją dwa sposoby, aby rozwiązać ten problem: ponownie instalację zdalnego debugowania i przez skopiowanie pliku do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszyny.

Ponowne uruchamianie konfiguracji zdalnego debugowania, postępuj zgodnie z instrukcjami w artykule [zdalne debugowanie](../debugger/remote-debugging.md).

Jeśli można znaleźć kopię Biblioteka ssdebugps.dll, możesz skopiować go na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszyny. Jeśli jest obecny, plik zostanie w \Program Files\ katalogu wspólnego Files\Microsoft Shared\SQL debugowania. Może okazać się na innym [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] komputerze lub na komputerze, na którym Visual Studio 2005.

Aby skopiować Biblioteka SSDEBUGPS.dll na komputerze programu SQL Server 2005:

1. Skopiuj plik do katalogu z taką samą nazwę i ścieżkę na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszyny.

2. Zarejestruj go, otwierając **polecenia**, a następnie uruchamiając następujące polecenie:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
