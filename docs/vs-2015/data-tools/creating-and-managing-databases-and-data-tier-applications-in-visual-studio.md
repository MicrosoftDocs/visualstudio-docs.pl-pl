---
title: Tworzenie baz danych i aplikacji warstwy danych oraz zarządzanie nimi
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
ms.openlocfilehash: 2d6ed13f2e21ea6b9da82eb47afefdd16088e71d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672461"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Tworzenie baz danych i aplikacji warstw danych oraz zarządzanie nimi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WAŻNE
> Projekty bazy danych uwzględnione we wcześniejszych wersjach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] są teraz dostępne w narzędziach [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)]. Aby uzyskać więcej informacji, zobacz [narzędzia SQL Server Developer](http://go.microsoft.com/fwlink/?LinkId=228126).

 Projekty bazy danych mogą służyć do tworzenia nowych baz danych, nowych aplikacji warstwy danych (DAC) oraz do aktualizowania istniejących baz danych i aplikacji warstwy danych. Zarówno projekty baz danych, jak i projekty DAC umożliwiają stosowanie kontroli wersji i technik zarządzania projektami do działań związanych z programowaniem bazy danych w podobny sposób, jak stosowanie tych technik do kodu zarządzanego lub natywnego. Aby ułatwić zespołowi programistycznemu zarządzanie zmianami baz danych i serwerów baz danych, można utworzyć *projekt DAC*, *projekt bazy danych*lub *projekt serwera* i umieścić go w kontroli wersji. Członkowie zespołu mogą następnie wyewidencjonowywać pliki, aby wprowadzać, kompilować i testować zmiany w *izolowanym środowisku programistycznym*lub piaskownicy przed udostępnieniem ich zespołowi. Aby zapewnić jakość kodu, zespół może zakończyć i przetestować wszystkie zmiany dotyczące konkretnej wersji bazy danych w środowisku przejściowym przed wdrożeniem zmian do produkcji.

 Listę funkcji bazy danych obsługiwanych przez aplikacje warstwy danych można znaleźć [w temacie Funkcje obsługiwane w aplikacjach warstwy danych](http://go.microsoft.com/fwlink/?LinkId=164239) w witrynie sieci Web firmy Microsoft. W przypadku korzystania z funkcji w bazie danych, które nie są obsługiwane przez aplikacje warstwy danych, należy zamiast tego użyć projektu bazy danych do zarządzania zmianami w bazie danych.

## <a name="common-high-level-tasks"></a>Typowe zadania wysokiego poziomu

|Zadanie wysokiego poziomu|Zawartość pomocnicza|
|----------------------|------------------------|
|**Rozpocznij programowanie aplikacji warstwy danych:** DAC to nowe koncepcje wprowadzone z [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)], które zawierają definicje dla bazy danych [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] i pomocniczych obiektów wystąpienia, które są używane przez aplikację klient-serwer lub 3-warstwowa. DAC obejmuje obiekty bazy danych, takie jak tabele i widoki, wraz z obiektami wystąpienia, takimi jak logowania. @No__t_0 można użyć do utworzenia projektu DAC, skompilowania pliku pakietu DAC i wysłania tego pliku pakietu DAC do administratora bazy danych w celu wdrożenia w wystąpieniu aparatu bazy danych [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [tworzenia aplikacji warstwy danych i zarządzania nimi](http://go.microsoft.com/fwlink/?LinkId=160741) (witryna sieci Web firmy Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Wykonywanie iteracyjnego tworzenia bazy danych:** Jeśli jesteś deweloperem lub testerem, wyewidencjonujesz części projektu, a następnie zaktualizujesz je w izolowanym środowisku programistycznym. Korzystając z tego typu środowiska, można testować zmiany bez wpływu na innych członków zespołu. Po zakończeniu wprowadzania zmian sprawdź pliki z powrotem do kontroli wersji, gdzie inni członkowie zespołu mogą uzyskać zmiany i skompilować je i wdrożyć na serwerze testowym.|[edytory zapytań i tekstów -    (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (witryna sieci Web firmy Microsoft)<br />-   [debuger języka Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (witryna sieci Web firmy Microsoft)|
|Tworzenie **prototypów, weryfikowanie wyników testów i modyfikowanie skryptów i obiektów bazy danych:** Do wykonania jednego z tych typowych zadań można użyć edytora [!INCLUDE[tsql](../includes/tsql-md.md)].|[edytory zapytań i tekstów -    (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (witryna sieci Web firmy Microsoft)|

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
