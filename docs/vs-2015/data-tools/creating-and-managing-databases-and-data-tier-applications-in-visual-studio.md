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
> Projekty bazy danych uwzględnione we wcześniejszych wersjach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] są teraz dostępne w narzędziach [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)]. Aby uzyskać więcej informacji, zobacz [narzędzia SQL Server Developer](https://go.microsoft.com/fwlink/?LinkId=228126).

 Projekty baz danych można użyć do tworzenia nowych baz danych, nowe aplikacje warstwy danych (DAC) i aktualizowanie istniejących baz danych i aplikacji warstwy danych. Projekty bazy danych i projektami DAC umożliwiają zastosowanie technik zarządzania projekt i kontroli wersji do swoich wysiłków programistycznych bazy danych w podobny sposób zastosowania tych technik do kodu zarządzanego lub natywnego. Aby ułatwić zespołowi programistycznemu zarządzanie zmianami baz danych i serwerów baz danych, można utworzyć *projekt DAC*, *projekt bazy danych*lub *projekt serwera* i umieścić go w kontroli wersji. Członkowie zespołu mogą następnie wyewidencjonowywać pliki, aby wprowadzać, kompilować i testować zmiany w *izolowanym środowisku programistycznym*lub piaskownicy przed udostępnieniem ich zespołowi. Aby zapewnić jakość kodu, Twój zespół może zakończenie i przetestowanie wszystkich zmian dla konkretnej wersji bazy danych w środowisku przejściowym, przed wdrożeniem zmian w środowisku produkcyjnym.

 Listę funkcji bazy danych obsługiwanych przez aplikacje warstwy danych można znaleźć [w temacie Funkcje obsługiwane w aplikacjach warstwy danych](https://go.microsoft.com/fwlink/?LinkId=164239) w witrynie sieci Web firmy Microsoft. Jeśli korzystasz z funkcji w bazie danych, które nie są obsługiwane przez aplikacje warstwy danych, należy zamiast tego użyć projektu bazy danych, zarządzanie zmianami z bazą danych.

## <a name="common-high-level-tasks"></a>Typowe zadania wysokiego poziomu

|Ogólne zadania|Zawartość pomocnicza|
|----------------------|------------------------|
|**Rozpocznij programowanie aplikacji warstwy danych:** DAC to nowe koncepcje wprowadzone z [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)], które zawierają definicje dla bazy danych [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] i pomocniczych obiektów wystąpienia, które są używane przez aplikację klient-serwer lub 3-warstwowa. Aplikacji DAC programu zawiera obiekty bazy danych, takich jak tabele i widoki, wraz z wystąpienia jednostki, takie jak nazwy logowania. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] można użyć do utworzenia projektu DAC, skompilowania pliku pakietu DAC i wysłania tego pliku pakietu DAC do administratora bazy danych w celu wdrożenia w wystąpieniu aparatu bazy danych [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [tworzenia aplikacji warstwy danych i zarządzania nimi](https://go.microsoft.com/fwlink/?LinkId=160741) (witryna sieci Web firmy Microsoft)<br />-   [SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=227328)|
|**Wykonywanie iteracyjnego tworzenia bazy danych:** Jeśli jesteś deweloperem lub testerem, wyewidencjonujesz części projektu, a następnie zaktualizujesz je w izolowanym środowisku programistycznym. Za pomocą tego typu środowiska, możesz testować wprowadzane zmiany, bez wywierania wpływu na innych członków zespołu. Po zakończeniu wprowadzania zmian, możesz sprawdzić pliki do kontroli wersji, gdy inni członkowie zespołu mogą uzyskać zmiany i tworzyć i wdrażać je na serwer testowy.|[edytory zapytań i tekstów -   (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (witryna sieci Web firmy Microsoft)<br />-   [debuger języka Transact-SQL](https://go.microsoft.com/fwlink/?LinkId=227324) (witryna sieci Web firmy Microsoft)|
|Tworzenie **prototypów, weryfikowanie wyników testów i modyfikowanie skryptów i obiektów bazy danych:** Do wykonania jednego z tych typowych zadań można użyć edytora [!INCLUDE[tsql](../includes/tsql-md.md)].|[edytory zapytań i tekstów -   (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (witryna sieci Web firmy Microsoft)|

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
