---
title: Tworzenie i zarządzanie bazami danych i aplikacji warstwy danych
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2b1caf45235f9dd745841cb26a2fa10a148a7b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299643"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Tworzenie i zarządzanie bazami danych i aplikacji warstwy danych w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[WAŻNE]
> Projekty baz danych, które występowały we wcześniejszych wersjach programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] znajdują się teraz w [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] narzędzia. Aby uzyskać więcej informacji, zobacz [narzędzia dla deweloperów programu SQL Server](https://go.microsoft.com/fwlink/?LinkId=228126).

 Projekty baz danych można użyć do tworzenia nowych baz danych, nowe aplikacje warstwy danych (DAC) i aktualizowanie istniejących baz danych i aplikacji warstwy danych. Projekty bazy danych i projektami DAC umożliwiają zastosowanie technik zarządzania projekt i kontroli wersji do swoich wysiłków programistycznych bazy danych w podobny sposób zastosowania tych technik do kodu zarządzanego lub natywnego. Możesz pomóc zespołowi zarządzania zmianami z bazami danych i serwery baz danych, tworząc *projektu aplikacji DAC*, *projekt bazy danych*, lub *Projekt serwera* i umieszczając go w systemie kontroli wersji. Członkowie zespołu mogą zapoznać się z pliki, aby wprowadzić, tworzenie i testowanie zmian w *izolowane środowisko pracy*, lub piaskownicy przed udostępnieniem ich zespołowi. Aby zapewnić jakość kodu, Twój zespół może zakończenie i przetestowanie wszystkich zmian dla konkretnej wersji bazy danych w środowisku przejściowym, przed wdrożeniem zmian w środowisku produkcyjnym.

 Aby uzyskać listę funkcji bazy danych, które są obsługiwane przez aplikacje warstwy danych, zobacz [funkcje obsługiwane w aplikacji warstwy danych](https://go.microsoft.com/fwlink/?LinkId=164239) w witrynie sieci web firmy Microsoft. Jeśli korzystasz z funkcji w bazie danych, które nie są obsługiwane przez aplikacje warstwy danych, należy zamiast tego użyć projektu bazy danych, zarządzanie zmianami z bazą danych.

## <a name="common-high-level-tasks"></a>Typowe zadania wysokiego poziomu

|Ogólne zadania|Zawartość pomocnicza|
|----------------------|------------------------|
|**Rozpocznij tworzenie aplikacji warstwy danych:** DAC to nowe pojęcie wprowadzone w programie [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] zawierający definicję [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bazy danych i towarzyszące wystąpienia obiektów, które są używane przez serwer do klienta lub 3-warstwowej aplikacja. Aplikacji DAC programu zawiera obiekty bazy danych, takich jak tabele i widoki, wraz z wystąpienia jednostki, takie jak nazwy logowania. Możesz użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Aby utworzyć projekt aplikacji DAC, tworzenie pliku pakietu aplikacji DAC, a następnie wysyłać ten plik pakietu aplikacji DAC administrator bazy danych w celu wdrożenia na wystąpienie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aparatu bazy danych.|-   [Tworzenie i zarządzanie nimi aplikacji warstwy danych](https://go.microsoft.com/fwlink/?LinkId=160741) (witryna sieci web firmy Microsoft)<br />-   [SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=227328)|
|**Wykonywanie programowanie iteracyjne bazy danych:** Jeśli jesteś deweloperem lub tester, zapoznaj się z części projektu, a następnie zaktualizuj je w środowisku izolowanym rozwoju. Za pomocą tego typu środowiska, możesz testować wprowadzane zmiany, bez wywierania wpływu na innych członków zespołu. Po zakończeniu wprowadzania zmian, możesz sprawdzić pliki do kontroli wersji, gdy inni członkowie zespołu mogą uzyskać zmiany i tworzyć i wdrażać je na serwer testowy.|-   [Zapytania i edytorów tekstu (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (witryna sieci web firmy Microsoft)<br />-   [Debuger języka Transact-SQL](https://go.microsoft.com/fwlink/?LinkId=227324) (witryna sieci web firmy Microsoft)|
|**Tworzenie prototypów, sprawdzanie wyników testów i modyfikowania skryptów bazy danych i obiektów:** można użyć [!INCLUDE[tsql](../includes/tsql-md.md)] edytora, aby wykonać dowolne spośród tych wspólnych zadań.|-   [Zapytania i edytorów tekstu (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (witryna sieci web firmy Microsoft)|

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
