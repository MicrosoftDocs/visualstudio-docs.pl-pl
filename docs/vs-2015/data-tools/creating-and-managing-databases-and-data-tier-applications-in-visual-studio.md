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
ms.openlocfilehash: b793789e092b46f14db397c1f8aef4e98544f856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851685"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Tworzenie baz danych i aplikacji warstw danych oraz zarządzanie nimi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WAŻNE
> Projekty bazy danych, które zostały uwzględnione we wcześniejszych wersjach programu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] są teraz dostępne w [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] narzędziach. Aby uzyskać więcej informacji, zobacz [narzędzia SQL Server Developer](https://msdn.microsoft.com/library/hh272686(VS.103).aspx).

 Projekty bazy danych mogą służyć do tworzenia nowych baz danych, nowych aplikacji warstwy danych (DAC) oraz do aktualizowania istniejących baz danych i aplikacji warstwy danych. Zarówno projekty baz danych, jak i projekty DAC umożliwiają stosowanie kontroli wersji i technik zarządzania projektami do działań związanych z programowaniem bazy danych w podobny sposób, jak stosowanie tych technik do kodu zarządzanego lub natywnego. Aby ułatwić zespołowi programistycznemu zarządzanie zmianami baz danych i serwerów baz danych, można utworzyć *projekt DAC*, *projekt bazy danych*lub *projekt serwera* i umieścić go w kontroli wersji. Członkowie zespołu mogą następnie wyewidencjonowywać pliki, aby wprowadzać, kompilować i testować zmiany w *izolowanym środowisku programistycznym*lub piaskownicy przed udostępnieniem ich zespołowi. Aby zapewnić jakość kodu, zespół może zakończyć i przetestować wszystkie zmiany dotyczące konkretnej wersji bazy danych w środowisku przejściowym przed wdrożeniem zmian do produkcji.

 Listę funkcji bazy danych obsługiwanych przez aplikacje warstwy danych można znaleźć [w temacie Funkcje obsługiwane w aplikacjach warstwy danych](https://msdn.microsoft.com/library/ee362013(VS.100).aspx) w witrynie sieci Web firmy Microsoft. W przypadku korzystania z funkcji w bazie danych, które nie są obsługiwane przez aplikacje warstwy danych, należy zamiast tego użyć projektu bazy danych do zarządzania zmianami w bazie danych.

## <a name="common-high-level-tasks"></a>Typowe zadania wysokiego poziomu

|Zadanie wysokiego poziomu|Zawartość pomocnicza|
|----------------------|------------------------|
|**Rozpocznij programowanie aplikacji warstwy danych:** DAC to nowe koncepcje [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] , które zawiera definicje [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bazy danych i pomocniczych obiektów wystąpienia, które są używane przez aplikację klienta-serwer lub 3-warstwową. DAC obejmuje obiekty bazy danych, takie jak tabele i widoki, wraz z obiektami wystąpienia, takimi jak logowania. Można użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do utworzenia projektu DAC, skompilowania pliku pakietu DAC i wysłania tego pliku pakietu DAC do administratora bazy danych w celu wdrożenia w wystąpieniu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aparatu bazy danych.|-   [Tworzenie aplikacji warstwy danych](https://msdn.microsoft.com/library/ee361996(VS.100).aspx) (witryna sieci Web firmy Microsoft) i zarządzanie nimi<br />-   [SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(SQL.110).aspx)|
|**Wykonywanie iteracyjnego tworzenia bazy danych:** Jeśli jesteś deweloperem lub testerem, wyewidencjonujesz części projektu, a następnie zaktualizujesz je w izolowanym środowisku programistycznym. Korzystając z tego typu środowiska, można testować zmiany bez wpływu na innych członków zespołu. Po zakończeniu wprowadzania zmian sprawdź pliki z powrotem do kontroli wersji, gdzie inni członkowie zespołu mogą uzyskać zmiany i skompilować je i wdrożyć na serwerze testowym.|-   [Edytory zapytań i tekstu (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (witryna sieci Web firmy Microsoft)<br />-   [Debuger języka Transact-SQL](https://msdn.microsoft.com/library/cc645997(SQL.110).aspx) (witryna sieci Web firmy Microsoft)|
|Tworzenie **prototypów, weryfikowanie wyników testów i modyfikowanie skryptów i obiektów bazy danych:** [!INCLUDE[tsql](../includes/tsql-md.md)]Aby wykonać dowolne z tych typowych zadań, można użyć edytora.|-   [Edytory zapytań i tekstu (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (witryna sieci Web firmy Microsoft)|

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
