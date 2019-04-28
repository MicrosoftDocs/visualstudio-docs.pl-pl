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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 854105ea5d94f6d3b09ce73a23ec45ccab9e797c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850484"
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
