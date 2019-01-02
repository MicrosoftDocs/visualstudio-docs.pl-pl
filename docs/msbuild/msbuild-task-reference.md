---
title: Odwołanie do zadania MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77473f001d3d363309f1ac2403a146d0aa8124cf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53884727"
---
# <a name="msbuild-task-reference"></a>Odwołanie do zadania MSBuild
Zadania zapewniają kod, który jest uruchamiany w procesie kompilacji. Zadania na poniższej liście są dołączone [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Gdy [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] jest zainstalowany, dodatkowe zadania są dostępne, które są wykorzystywane do zorganizowania [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów. Aby uzyskać więcej informacji, zobacz [zadań Visual C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  

 Oprócz parametrów wymienionych w tematach w tej sekcji każde zadanie ma następujące parametry:  


| Parametr | Opis |
|-------------------| - |
| `Condition` | Opcjonalnie `String` parametru.<br /><br /> A `Boolean` wyrażenia, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aparat używa do określenia, czy to zadanie zostanie wykonany. Aby uzyskać informacje o warunkach, które są obsługiwane przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], zobacz [warunki](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Jeśli zadanie nie powiedzie się, kolejne zadania w [docelowej](../msbuild/target-element-msbuild.md) elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue**. Jeśli zadanie nie powiedzie się, kolejne zadania w `Target` elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (ustawienie domyślne). Jeśli zadanie nie powiedzie się, kolejnych zadań na `Target` elementu i kompilacja nie są wykonywane i całą `Target` elementu i kompilacja jest uważany za nie powiodło się.<br /><br /> Wersje programu .NET Framework przed 4.5 obsługiwane tylko `true` i `false` wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>W tej sekcji  
 [Klasa podstawowa zadania](../msbuild/task-base-class.md)  
 Dodaje kilka parametrów do zadań, które wynikają z <xref:Microsoft.Build.Utilities.Task> klasy.  

 [Taskextension — klasa bazowa](../msbuild/taskextension-base-class.md)  
 Dodaje kilka parametrów do zadań, które wynikają z <xref:Microsoft.Build.Tasks.TaskExtension> klasy.  

 [Tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md)  
 Dodaje kilka parametrów do zadań, które wynikają z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy.  

 [AL (Assembly Linker) zadanie](../msbuild/al-assembly-linker-task.md)  
 Tworzy zestaw z manifestem z co najmniej jeden plik, który jest modułem lub plikiem zasobów.  

 [Aspnetcompiler — zadanie](../msbuild/aspnetcompiler-task.md)  
 Opakowuje *aspnet_compiler.exe*, narzędzie wstępnej kompilacji aplikacji ASP.NET.  

 [Assignculture — zadanie](../msbuild/assignculture-task.md)  
 Przypisuje identyfikatory kultury elementów.  

 [Assignprojectconfiguration — zadanie](../msbuild/assignprojectconfiguration-task.md)  
 Akceptuje ciągi konfiguracji listy i przypisuje je do określonych projektów.  

 [Assigntargetpath — zadanie](../msbuild/assigntargetpath-task.md)  
 Akceptuje listę plików i dodaje `<TargetPath>` atrybuty, jeśli nie są już określone.  

 [Calltarget — zadanie](../msbuild/calltarget-task.md)  
 Wywołuje element docelowy w pliku projektu.  

 [Combinepath — zadanie](../msbuild/combinepath-task.md)  
 Łączy określonych ścieżek w pojedynczą ścieżkę.  

 [Converttoabsolutepath — zadanie](../msbuild/converttoabsolutepath-task.md)  
 Konwertuje ścieżką względną lub odwołanie do ścieżki bezwzględnej.  

 [Copy — zadanie](../msbuild/copy-task.md)  
 Kopiuje pliki do nowej lokalizacji.  

 [Createcsharpmanifestresourcename — zadanie](../msbuild/createcsharpmanifestresourcename-task.md)  
 Tworzy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]— styl nazwy manifestu z danym *resx* nazwa pliku lub innego zasobu.  

 [Createitem — zadanie](../msbuild/createitem-task.md)  
 Wypełnia kolekcji elementów z elementów wejściowych, umożliwiając elementy, które mają być kopiowane z jednej listy do innej.  

 [CreateProperty — zadanie](../msbuild/createproperty-task.md)  
 Wypełnia właściwości z wartości wejściowych, dzięki czemu wartości, które mają być kopiowane z jedną właściwość lub ciągu do innego.  

 [Createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Tworzy [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]— styl nazwy manifestu z danym *resx* nazwa pliku lub innego zasobu.  

 [CSC — zadanie](../msbuild/csc-task.md)  
 Wywołuje kompilatora Visual C#, aby wygenerować pliki wykonywalne, bibliotek dołączanych dynamicznie lub modułów kodu.  

 [Delete — zadanie](../msbuild/delete-task.md)  
 Usuwa określone pliki.  

 [Zadanie DownloadFile](../msbuild/downloadfile-task.md)  
 Pobiera plik do określonej lokalizacji.  

 [Error — zadanie](../msbuild/error-task.md)  
 Zatrzymuje kompilację i rejestruje błąd oparte na ocenianą instrukcji warunkowej.  

 [Exec — zadanie](../msbuild/exec-task.md)  
 Uruchamia określony program lub polecenie z określonymi argumentami.  

 [Findappconfigfile — zadanie](../msbuild/findappconfigfile-task.md)  
 Umożliwia znalezienie *app.config* plik w podanej listy.  

 [Findinlist — zadanie](../msbuild/findinlist-task.md)  
 Wyszukuje element w określonej listy, która ma pasujące itemspec.  

 [Findunderpath — zadanie](../msbuild/findunderpath-task.md)  
 Określa, które elementy w kolekcji określony element istnieje w określonym folderze i wszystkich jego podfolderów.  

 [Formaturl — zadanie](../msbuild/formaturl-task.md)  
 Konwertuje adres URL do poprawnego formatu adresu URL.  

 [Formatversion — zadanie](../msbuild/formatversion-task.md)  
 Dołącza numer wersji do numeru wersji.  

 [Generateapplicationmanifest — zadanie](../msbuild/generateapplicationmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji lub manifest macierzysty.  

 [Generatebootstrapper — zadanie](../msbuild/generatebootstrapper-task.md)  
 Umożliwia automatyczne wykrywanie, pobieranie i instalowanie aplikacji i jej wstępnie wymagane składniki.  

 [Generatedeploymentmanifest — zadanie](../msbuild/generatedeploymentmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrożenia.  

 [Generateresource — zadanie](../msbuild/generateresource-task.md)  
 Konwertuje *.txt* i *resx* plików środowiska uruchomieniowego języka wspólnego binarne *Resources* plików.  

 [Generatetrustinfo — zadanie](../msbuild/generatetrustinfo-task.md)  
 Generuje zaufanie aplikacji z manifestu podstawowej oraz `TargetZone` i `ExcludedPermissions` parametrów.  

 [Getassemblyidentity — zadanie](../msbuild/getassemblyidentity-task.md)  
 Pobiera tożsamość zestawu z określonych plików i wyświetla informacje o tożsamości.  

 [Getframeworkpath — zadanie](../msbuild/getframeworkpath-task.md)  
 Pobiera ścieżkę do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zestawów.  

 [Getframeworksdkpath — zadanie](../msbuild/getframeworksdkpath-task.md)  
 Pobiera ścieżkę do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  

 [Getreferenceassemblypaths — zadanie](../msbuild/getreferenceassemblypaths-task.md)  
 Zwraca odwołanie ścieżki zestawów w różnych architektur.  

 [LC — zadanie](../msbuild/lc-task.md)  
 Generuje *.license* plik wchodzącej w skład *licx* pliku.  

 [Makedir — zadanie](../msbuild/makedir-task.md)  
 Tworzy katalogów i, jeśli to konieczne, dominujące katalogów.  

 [Komunikat — zadanie](../msbuild/message-task.md)  
 Rejestruje komunikat podczas kompilacji.  

 [MOVE — zadanie](../msbuild/move-task.md)  
 Przenosi pliki do nowej lokalizacji.  

 [Zadanie MSBuild](../msbuild/msbuild-task.md)  
 Kompilacje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów z innego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu.  

 [Readlinesfromfile — zadanie](../msbuild/readlinesfromfile-task.md)  
 Odczytuje listę elementów z pliku tekstowego.  

 [Registerassembly — zadanie](../msbuild/registerassembly-task.md)  
 Odczytuje metadane w określonym zestawie i dodaje niezbędne wpisy do rejestru.  

 [Removedir — zadanie](../msbuild/removedir-task.md)  
 Usuwa określony katalog i wszystkie jego pliki i podkatalogi.  

 [Removeduplicates — zadanie](../msbuild/removeduplicates-task.md)  
 Usuwa zduplikowane elementy z kolekcji określonego elementu.  

 [Requiresframework35sp1assembly — zadanie](../msbuild/requiresframework35sp1assembly-task.md)  
 Określa, czy aplikacja wymaga .NET Framework 3.5 SP1.  

 Zadanie ResGen  
 Nieaktualne. Użyj [generateresource — zadanie](../msbuild/generateresource-task.md) zadanie, aby przekonwertować *.txt* i *resx* plików do i z środowiska uruchomieniowego języka wspólnego binarne *Resources* pliki.  

 [Resolveassemblyreference — zadanie](../msbuild/resolveassemblyreference-task.md)  
 Określa wszystkie zestawy, które są zależne od określonych zestawów.  

 [Resolvecomreference — zadanie](../msbuild/resolvecomreference-task.md)  
 Przyjmuje listę wpisz jeden lub więcej nazw bibliotek lub *.tlb* pliki i jest rozpoznawana jako tych bibliotek typów do lokalizacji na dysku.  

 [Resolvekeysource — zadanie](../msbuild/resolvekeysource-task.md)  
 Określa źródło klucza silnej nazwy  

 [Resolvemanifestfiles — zadanie](../msbuild/resolvemanifestfiles-task.md)  
 Jest rozpoznawana jako następujące elementy w procesie kompilacji plików do generowania manifestu: wbudowane elementy, zależności, satelity, zawartość, symbole debugowania i dokumentację.  

 [Resolvenativereference — zadanie](../msbuild/resolvenativereference-task.md)  
 Usuwa odwołania natywne.  

 [Resolvenonmsbuildprojectoutput — zadanie](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Określa pliki wyjściowe dla odwołań do projektu niekorzystających z programu MSBuild.  

 [SGen — zadanie](../msbuild/sgen-task.md)  
 Tworzy zestaw serializacji XML dla typów w określonym zestawie.  

 [Signfile — zadanie](../msbuild/signfile-task.md)  
 Podpisuje określonego pliku przy użyciu określonego certyfikatu.  

 [Touch — zadanie](../msbuild/touch-task.md)  
 Ustawia czas dostępu i modyfikacji plików.  

 [Unregisterassembly — zadanie](../msbuild/unregisterassembly-task.md)  
 Wyrejestrowuje określonych zestawów do celów międzyoperacyjności COM.  

 [Rozpakuj zadania](../msbuild/unzip-task.md)  
 Unzips *zip* archiwum do określonej lokalizacji.

 [Updatemanifest — zadanie](../msbuild/updatemanifest-task.md)  
 Aktualizuje właściwości wybranego w manifeście i rezygnuje.  

 [Vbc — zadanie](../msbuild/vbc-task.md)  
 Wywołuje kompilator języka Visual Basic generuje pliki wykonywalne, bibliotek dołączanych dynamicznie lub modułów kodu...  

 [Warning — zadanie](../msbuild/warning-task.md)  
 Dzienniki ostrzeżenie podczas kompilacji w oparciu ocenianą instrukcji warunkowej.  

 [Writecodefragment — zadanie](../msbuild/writecodefragment-task.md)  
 Generuje plik tymczasowy kod, za pomocą fragmentu określonego wygenerowanego kodu. Nie powoduje usunięcia pliku.  

 [Writelinestofile — zadanie](../msbuild/writelinestofile-task.md)  
 Zapisuje określone elementy do pliku określony tekst.  

 [Xmlpeek — zadanie](../msbuild/xmlpeek-task.md)  
 Zwraca wartości określonych przez zapytanie XPath z pliku XML.  

 [Xmlpoke — zadanie](../msbuild/xmlpoke-task.md)  
 Ustawia wartości określonych przez zapytanie XPath do pliku XML.  

 [Xsltransformation — zadanie](../msbuild/xsltransformation-task.md)  
 Przekształca dane wejściowe XML przy użyciu *Extensible arkusza stylów języka przekształcenia* (XSLT) lub obliczonych XSLT i dane wyjściowe do wyjścia urządzenia lub pliku.  

  [Zadanie ZipDirectory](../msbuild/zipdirectory-task.md)  
 Tworzy *zip* archiwum z zawartości katalogu.

## <a name="see-also"></a>Zobacz także  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Wpisywanie zadania](../msbuild/task-writing.md)   
 [Zadania](../msbuild/msbuild-tasks.md)