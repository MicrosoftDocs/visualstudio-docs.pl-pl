---
title: Przed kompilacją wiersz polecenia zdarzenia zdarzenie po kompilacji, okno dialogowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 213535d983f95f304b8e0fba3241fa502577f0f4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438055"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Wiersz polecenia zdarzenia sprzed kompilacji/zdarzenia po kompilacji — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Możesz wpisać zdarzenia przed lub po kompilacji dla [zdarzenia Stroka kompilacji, Projektant projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) bezpośrednio w edycji pola, użytkownik może wybrać makra przed i po kompilacji z listy dostępnych makr.  
  
> [!NOTE]
> Jeśli projekt jest aktualny, a nie kompilacja zostaje wyzwolona, nie należy uruchamiać zdarzenia prekompilacyjnego.  
  
## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika  
 **Pole edycji wiersza polecenia**  
 Zawiera zdarzenia do uruchomienia kompilacji przed lub po kompilacji.  
  
> [!NOTE]
> Dodaj `call` instrukcję przed polecenia wszystkich wykonywanych po kompilacji, które uruchamiają pliki bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Makra**  
 Rozwijane pole edycji, aby wyświetlić listę makra do wstawienia w polu edycji wiersza polecenia.  
  
 **Tabela — makro**  
 Wyświetla listę dostępnych makr oraz jego wartość. Opis każdego z nich, zobacz makra poniżej. Można wybrać tylko jedną — makro w czasie do wstawienia w polu edycji wiersza polecenia.  
  
 **Wstaw**  
 Operacje wstawiania do wiersza polecenia Edytuj pola po wybraniu makra w tabeli — makro.  
  
### <a name="macros"></a>Makra  
 Można użyć dowolnego z tych makr, określ lokalizację plików lub uzyskać rzeczywistą nazwę pliku wejściowego w przypadku zaznaczenia wielu. Te makra nie jest rozróżniana wielkość liter.  
  
|Macro|Opis|  
|-----------|-----------------|  
|`$(ConfigurationName)`|Nazwa bieżącej konfiguracji projektu, na przykład "Debug".|  
|`$(OutDir)`|Ścieżka do katalogu pliku wyjściowego względem katalogu projektu. To jest rozpoznawana jako wartość właściwości katalogu wyjściowego. Zawiera ukośnik odwrotny na końcu "\\".|  
|`$(DevEnvDir)`|Katalogu instalacyjnego programu Visual Studio (zdefiniowane przy użyciu dysku i ścieżki); zawiera ukośnik odwrotny na końcu "\\".|  
|`$(PlatformName)`|Nazwa obecnie docelowej platformy. Na przykład "AnyCPU".|  
|`$(ProjectDir)`|Katalogu projektu (zdefiniowane przy użyciu dysku i ścieżki); zawiera ukośnik odwrotny na końcu "\\".|  
|`$(ProjectPath)`|Nazwa ścieżki bezwzględnej projektu (zdefiniowanych za pomocą dysku, ścieżka, nazwa podstawowa i rozszerzenie pliku).|  
|`$(ProjectName)`|Podstawowa nazwa projektu.|  
|`$(ProjectFileName)`|Nazwa pliku projektu (zdefiniowany z podstawowej nazwy pliku rozszerzenie).|  
|`$(ProjectExt)`|Rozszerzenie pliku projektu. Zawiera on "." przed rozszerzeniem pliku.|  
|`$(SolutionDir)`|Katalog rozwiązania (zdefiniowane przy użyciu dysku i ścieżki); zawiera ukośnik odwrotny na końcu "\\".|  
|`$(SolutionPath)`|Nazwa ścieżki bezwzględnej rozwiązania (zdefiniowanych za pomocą dysku, ścieżka, nazwa podstawowa i rozszerzenie pliku).|  
|`$(SolutionName)`|Podstawowa nazwa rozwiązania.|  
|`$(SolutionFileName)`|Nazwa pliku rozwiązania (zdefiniowany z podstawowej nazwy pliku rozszerzenie).|  
|`$(SolutionExt)`|Rozszerzenie pliku rozwiązania. Zawiera on "." przed rozszerzeniem pliku.|  
|`$(TargetDir)`|Katalog pliku główny wynik kompilacji (zdefiniowane przy użyciu dysku i ścieżki). Zawiera ukośnik odwrotny na końcu "\\".|  
|`$(TargetPath)`|Nazwa ścieżki bezwzględnej plik główny wynik kompilacji (zdefiniowanych za pomocą dysku, ścieżka, nazwa podstawowa i rozszerzenie pliku).|  
|`$(TargetName)`|Podstawowa nazwa pliku wyjściowego podstawowej dla kompilacji.|  
|`$(TargetFileName)`|Nazwa pliku plik główny wynik kompilacji (zdefiniowany jako podstawowa nazwa i rozszerzenie).|  
|`$(TargetExt)`|Rozszerzenie pliku plik główny wynik kompilacji. Zawiera on "." przed rozszerzeniem pliku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie niestandardowych zdarzeń kompilacji w programie Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [Strona zdarzenia kompilacji, Projektant projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)   
 [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Instrukcje: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)
