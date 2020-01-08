---
title: Projekty bazy danych i projekty DAC
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc8d32ddcc332264278cf76392ac69a6188ca51c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586734"
---
# <a name="database-projects-and-data-tier-applications"></a>Projekty bazy danych i aplikacje warstwy danych

Projekty baz danych można użyć do tworzenia nowych baz danych, nowe aplikacje warstwy danych (DAC) i aktualizowanie istniejących baz danych i aplikacji warstwy danych. Projekty bazy danych i projektami DAC umożliwiają zastosowanie technik zarządzania projekt i kontroli wersji do swoich wysiłków programistycznych bazy danych w podobny sposób zastosowania tych technik do kodu zarządzanego lub natywnego. Aby ułatwić zespołowi programistycznemu zarządzanie zmianami baz danych i serwerów baz danych, można utworzyć projekt DAC, projekt bazy danych lub projekt serwera i umieścić go w kontroli wersji. Członkowie zespołu mogą następnie wyewidencjonowywać pliki, aby wprowadzać, kompilować i testować zmiany w izolowanym środowisku programistycznym lub piaskownicy przed udostępnieniem ich zespołowi. Aby zapewnić jakość kodu, Twój zespół może zakończenie i przetestowanie wszystkich zmian dla konkretnej wersji bazy danych w środowisku przejściowym, przed wdrożeniem zmian w środowisku produkcyjnym.

Listę funkcji bazy danych obsługiwanych przez aplikacje warstwy danych można znaleźć w temacie [Obsługa programu DAC dla SQL Server obiektów](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). W przypadku korzystania z funkcji w bazie danych, które nie są obsługiwane przez aplikacje warstwy danych, należy zamiast tego użyć projektu bazy danych do zarządzania zmianami w bazie danych.

## <a name="common-high-level-tasks"></a>Typowe zadania wysokiego poziomu

| Ogólne zadania | Zawartość pomocnicza |
| - | - |
| **Rozpocznij programowanie aplikacji warstwy danych:** Koncepcja aplikacji warstwy danych (DAC) została wprowadzona w SQL Server 2008. DAC zawiera definicję bazy danych SQL Server i pomocniczych obiektów wystąpienia, które są używane przez aplikację klient-serwer lub 3-warstwowa. Aplikacji DAC programu zawiera obiekty bazy danych, takich jak tabele i widoki, wraz z wystąpienia jednostki, takie jak nazwy logowania. Możesz użyć programu Visual Studio do utworzenia projektu DAC, skompilowania pliku pakietu DAC i wysłania pliku pakietu DAC do administratora bazy danych w celu wdrożenia w wystąpieniu aparatu bazy danych SQL Server. | - [aplikacji warstwy danych](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Wykonywanie iteracyjnego tworzenia bazy danych:** Deweloperzy mogą wyewidencjonowywać części projektu i aktualizować je w izolowanym środowisku programistycznym. Korzystając z tego typu środowiska, można testować zmiany bez wpływu na innych członków zespołu. Po zakończeniu wprowadzania zmian, możesz sprawdzić pliki do kontroli wersji, gdy inni członkowie zespołu mogą uzyskać zmiany i tworzyć i wdrażać je na serwer testowy. | - [projektowanie zorientowane na projekt w trybie offline (narzędzia danych SQL Server)](/sql/ssdt/project-oriented-offline-database-development)<br />- [debuger języka Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| Tworzenie **prototypów, weryfikowanie wyników testów i modyfikowanie skryptów i obiektów bazy danych:** Za pomocą edytora języka Transact-SQL można wykonać dowolne z tych typowych zadań. | - [edytorów zapytań i tekstu (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
