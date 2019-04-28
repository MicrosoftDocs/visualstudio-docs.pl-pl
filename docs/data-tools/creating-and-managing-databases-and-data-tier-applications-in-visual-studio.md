---
title: Projekty baz danych i projektami DAC
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2a86d9511e470c9a810ff58e80e4cae1f9a0cb11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567243"
---
# <a name="database-projects-and-data-tier-applications"></a>Projekty baz danych i aplikacji warstwy danych

Projekty baz danych można użyć do tworzenia nowych baz danych, nowe aplikacje warstwy danych (DAC) i aktualizowanie istniejących baz danych i aplikacji warstwy danych. Projekty bazy danych i projektami DAC umożliwiają zastosowanie technik zarządzania projekt i kontroli wersji do swoich wysiłków programistycznych bazy danych w podobny sposób zastosowania tych technik do kodu zarządzanego lub natywnego. Możesz pomóc zespołowi zarządzania zmianami z bazami danych i serwery baz danych przez tworzenie projektu aplikacji DAC, projekt bazy danych lub server project i umieszczenie go w systemie kontroli wersji. Członkowie zespołu mogą następnie wyewidencjonowywanie plików do wprowadzić, tworzenie i testowanie zmian w środowisko programistyczne izolowanej lub piaskownicy, przed udostępnieniem ich zespołowi. Aby zapewnić jakość kodu, Twój zespół może zakończenie i przetestowanie wszystkich zmian dla konkretnej wersji bazy danych w środowisku przejściowym, przed wdrożeniem zmian w środowisku produkcyjnym.

Aby uzyskać listę funkcji bazy danych, które są obsługiwane przez aplikacje warstwy danych, zobacz [DAC obsługi dla obiektów programu SQL Server](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Jeśli korzystasz z funkcji w bazie danych, które nie są obsługiwane przez aplikacje warstwy danych, należy zamiast tego użyć projektu bazy danych, zarządzanie zmianami z bazą danych.

## <a name="common-high-level-tasks"></a>Typowe zadania wysokiego poziomu

| Ogólne zadania | Zawartość pomocnicza |
| - | - |
| **Rozpocznij tworzenie aplikacji warstwy danych:** Pojęcie aplikacji warstwy danych (DAC) została wprowadzona w programie SQL Server 2008. Aplikacji DAC programu zawiera definicję dla bazy danych programu SQL Server i pomocnicze obiekty wystąpienia, które są używane przez serwer do klienta lub aplikacji 3-warstwowej. Aplikacji DAC programu zawiera obiekty bazy danych, takich jak tabele i widoki, wraz z wystąpienia jednostki, takie jak nazwy logowania. Za pomocą programu Visual Studio Utwórz projekt aplikacji DAC, tworzenie pliku pakietu aplikacji DAC i wysyłać plik pakietu aplikacji DAC administrator bazy danych w celu wdrożenia na wystąpienie aparatu bazy danych programu SQL Server. | - [Aplikacje warstwy danych](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Wykonywanie programowanie iteracyjne bazy danych:** Deweloperzy mogą zapoznaj się z części projektu i zaktualizować je w środowisku izolowanym rozwoju. Za pomocą tego typu środowiska, możesz testować wprowadzane zmiany, bez wywierania wpływu na innych członków zespołu. Po zakończeniu wprowadzania zmian, możesz sprawdzić pliki do kontroli wersji, gdy inni członkowie zespołu mogą uzyskać zmiany i tworzyć i wdrażać je na serwer testowy. | - [Programowanie zorientowane na projekt bazy danych w trybie offline (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Debuger języka Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Tworzenie prototypów sprawdzanie wyników testów i modyfikowania skryptów bazy danych i obiektów:** Aby wykonać dowolne spośród tych wspólnych zadań, można użyć edytora języka Transact-SQL. | - [Edytory zapytania i tekst (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)