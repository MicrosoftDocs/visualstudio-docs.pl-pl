---
title: Odwołanie do zadania MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bd6df873bf1aadbec4b12763369c60f127819c0
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834426"
---
# <a name="msbuild-task-reference"></a>Odwołanie do zadania MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zadania zapewniają kod, który jest uruchamiany w procesie kompilacji. Zadania na poniższej liście są dołączone [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Gdy [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] jest zainstalowany, dodatkowe zadania są dostępne, które są wykorzystywane do zorganizowania [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektów. Aby uzyskać więcej informacji, zobacz [Visual C++ zadania](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Oprócz parametrów wymienionych w tematach w tej sekcji każde zadanie ma następujące parametry:  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Condition`|Opcjonalnie `String` parametru.<br /><br /> A `Boolean` wyrażenia, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aparat używa do określenia, czy to zadanie zostanie wykonany. Aby uzyskać informacje o warunkach, które są obsługiwane przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Jeśli zadanie nie powiedzie się, kolejne zadania w [docelowej](../msbuild/target-element-msbuild.md) elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue**. Jeśli zadanie nie powiedzie się, kolejne zadania w `Target` elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (ustawienie domyślne). Jeśli zadanie nie powiedzie się, kolejnych zadań na `Target` elementu i kompilacja nie są wykonywane i całą `Target` elementu i kompilacja jest uważany za nie powiodło się.<br /><br /> Wersje programu .NET Framework przed 4.5 obsługiwane tylko `true` i `false` wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Klasa podstawowa zadania](../msbuild/task-base-class.md)  
 Dodaje kilka parametrów do zadań, które wynikają z <xref:Microsoft.Build.Utilities.Task> klasy.  
  
 [TaskExtension, klasa podstawowa](../msbuild/taskextension-base-class.md)  
 Dodaje kilka parametrów do zadań, które wynikają z <xref:Microsoft.Build.Tasks.TaskExtension> klasy.  
  
 [ToolTaskExtension, klasa podstawowa](../msbuild/tooltaskextension-base-class.md)  
 Dodaje kilka parametrów do zadań, które wynikają z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy.  
  
 [AL (Assembly Linker), zadanie](../msbuild/al-assembly-linker-task.md)  
 Tworzy zestaw z manifestem z co najmniej jeden plik, który jest modułem lub plikiem zasobów.  
  
 [AspNetCompiler, zadanie](../msbuild/aspnetcompiler-task.md)  
 Opakowuje aspnet_compiler.exe, narzędzie wstępnej kompilacji aplikacji ASP.NET.  
  
 [AssignCulture, zadanie](../msbuild/assignculture-task.md)  
 Przypisuje identyfikatory kultury elementów.  
  
 [AssignProjectConfiguration, zadanie](../msbuild/assignprojectconfiguration-task.md)  
 Akceptuje ciągi konfiguracji listy i przypisuje je do określonych projektów.  
  
 [AssignTargetPath, zadanie](../msbuild/assigntargetpath-task.md)  
 Akceptuje listę plików i dodaje `<TargetPath>` atrybuty, jeśli nie są już określone.  
  
 [CallTarget, zadanie](../msbuild/calltarget-task.md)  
 Wywołuje element docelowy w pliku projektu.  
  
 [CombinePath, zadanie](../msbuild/combinepath-task.md)  
 Łączy określonych ścieżek w pojedynczą ścieżkę.  
  
 [ConvertToAbsolutePath, zadanie](../msbuild/converttoabsolutepath-task.md)  
 Konwertuje ścieżką względną lub odwołanie do ścieżki bezwzględnej.  
  
 [Copy, zadanie](../msbuild/copy-task.md)  
 Kopiuje pliki do nowej lokalizacji.  
  
 [CreateCSharpManifestResourceName, zadanie](../msbuild/createcsharpmanifestresourcename-task.md)  
 Tworzy [!INCLUDE[csprcs](../includes/csprcs-md.md)]— styl nazwy manifestu z nazwę pliku ResX danego lub innego zasobu.  
  
 [CreateItem, zadanie](../msbuild/createitem-task.md)  
 Wypełnia kolekcji elementów z elementów wejściowych, umożliwiając elementy, które mają być kopiowane z jednej listy do innej.  
  
 [CreateProperty, zadanie](../msbuild/createproperty-task.md)  
 Wypełnia właściwości z wartości wejściowych, dzięki czemu wartości, które mają być kopiowane z jedną właściwość lub ciągu do innego.  
  
 [CreateVisualBasicManifestResourceName, zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Tworzy [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]— styl nazwy manifestu z nazwę pliku ResX danego lub innego zasobu.  
  
 [Csc, zadanie](../msbuild/csc-task.md)  
 Wywołuje kompilatora Visual C#, aby wygenerować pliki wykonywalne, bibliotek dołączanych dynamicznie lub modułów kodu.  
  
 [Delete, zadanie](../msbuild/delete-task.md)  
 Usuwa określone pliki.  
  
 [Error, zadanie](../msbuild/error-task.md)  
 Zatrzymuje kompilację i rejestruje błąd oparte na ocenianą instrukcji warunkowej.  
  
 [Exec, zadanie](../msbuild/exec-task.md)  
 Uruchamia określony program lub polecenie z określonymi argumentami.  
  
 [FindAppConfigFile, zadanie](../msbuild/findappconfigfile-task.md)  
 Umożliwia znalezienie pliku app.config, w podanej listy.  
  
 [FindInList, zadanie](../msbuild/findinlist-task.md)  
 Wyszukuje element w określonej listy, która ma pasujące itemspec.  
  
 [FindUnderPath, zadanie](../msbuild/findunderpath-task.md)  
 Określa, które elementy w kolekcji określony element istnieje w określonym folderze i wszystkich jego podfolderów.  
  
 [FormatUrl, zadanie](../msbuild/formaturl-task.md)  
 Konwertuje adres URL do poprawnego formatu adresu URL.  
  
 [FormatVersion, zadanie](../msbuild/formatversion-task.md)  
 Dołącza numer wersji do numeru wersji.  
  
 [GenerateApplicationManifest, zadanie](../msbuild/generateapplicationmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikacji lub manifest macierzysty.  
  
 [GenerateBootstrapper, zadanie](../msbuild/generatebootstrapper-task.md)  
 Umożliwia automatyczne wykrywanie, pobieranie i instalowanie aplikacji i jej wstępnie wymagane składniki.  
  
 [GenerateDeploymentManifest, zadanie](../msbuild/generatedeploymentmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest wdrożenia.  
  
 [GenerateResource, zadanie](../msbuild/generateresource-task.md)  
 Konwertuje pliki txt i resx wspólne pliki binarne Resources środowiska uruchomieniowego języka.  
  
 [GenerateTrustInfo, zadanie](../msbuild/generatetrustinfo-task.md)  
 Generuje zaufanie aplikacji z manifestu podstawowej oraz `TargetZone` i `ExcludedPermissions` parametrów.  
  
 [GetAssemblyIdentity, zadanie](../msbuild/getassemblyidentity-task.md)  
 Pobiera tożsamość zestawu z określonych plików i wyświetla informacje o tożsamości.  
  
 [GetFrameworkPath, zadanie](../msbuild/getframeworkpath-task.md)  
 Pobiera ścieżkę do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zestawów.  
  
 [GetFrameworkSdkPath, zadanie](../msbuild/getframeworksdkpath-task.md)  
 Pobiera ścieżkę do [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
 [GetReferenceAssemblyPaths, zadanie](../msbuild/getreferenceassemblypaths-task.md)  
 Zwraca odwołanie ścieżki zestawów w różnych architektur.  
  
 [LC, zadanie](../msbuild/lc-task.md)  
 Generuje plik .license z pliku licx.  
  
 [MakeDir, zadanie](../msbuild/makedir-task.md)  
 Tworzy katalogów i, jeśli to konieczne, dominujące katalogów.  
  
 [Message, zadanie](../msbuild/message-task.md)  
 Rejestruje komunikat podczas kompilacji.  
  
 [Move, zadanie](../msbuild/move-task.md)  
 Przenosi pliki do nowej lokalizacji.  
  
 [MSBuild, zadanie](../msbuild/msbuild-task.md)  
 Kompilacje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektów z innego [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu.  
  
 [ReadLinesFromFile, zadanie](../msbuild/readlinesfromfile-task.md)  
 Odczytuje listę elementów z pliku tekstowego.  
  
 [RegisterAssembly, zadanie](../msbuild/registerassembly-task.md)  
 Odczytuje metadane w określonym zestawie i dodaje niezbędne wpisy do rejestru.  
  
 [RemoveDir, zadanie](../msbuild/removedir-task.md)  
 Usuwa określony katalog i wszystkie jego pliki i podkatalogi.  
  
 [RemoveDuplicates, zadanie](../msbuild/removeduplicates-task.md)  
 Usuwa zduplikowane elementy z kolekcji określonego elementu.  
  
 [RequiresFramework35SP1Assembly, zadanie](../msbuild/requiresframework35sp1assembly-task.md)  
 Określa, czy aplikacja wymaga .NET Framework 3.5 SP1.  
  
 Zadanie ResGen  
 Nieaktualne. Użyj [generateresource — zadanie](../msbuild/generateresource-task.md) zadanie, aby skonwertować txt i resx do i z common language runtime binarnych plików Resources.  
  
 [ResolveAssemblyReference, zadanie](../msbuild/resolveassemblyreference-task.md)  
 Określa wszystkie zestawy, które są zależne od określonych zestawów.  
  
 [ResolveCOMReference, zadanie](../msbuild/resolvecomreference-task.md)  
 Przyjmuje listę nazw bibliotek typów lub plików .tlb i jest rozpoznawana jako tych bibliotek typów do lokalizacji na dysku.  
  
 [ResolveKeySource, zadanie](../msbuild/resolvekeysource-task.md)  
 Określa źródło klucza silnej nazwy  
  
 [ResolveManifestFiles, zadanie](../msbuild/resolvemanifestfiles-task.md)  
 Jest rozpoznawana jako następujące elementy w procesie kompilacji plików do generowania manifestu: wbudowane elementy, zależności, satelity, zawartość, symbole debugowania i dokumentację.  
  
 [ResolveNativeReference, zadanie](../msbuild/resolvenativereference-task.md)  
 Usuwa odwołania natywne.  
  
 [ResolveNonMSBuildProjectOutput, zadanie](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Określa pliki wyjściowe dla odwołań do projektu niekorzystających z programu MSBuild.  
  
 [SGen, zadanie](../msbuild/sgen-task.md)  
 Tworzy zestaw serializacji XML dla typów w określonym zestawie.  
  
 [SignFile, zadanie](../msbuild/signfile-task.md)  
 Podpisuje określonego pliku przy użyciu określonego certyfikatu.  
  
 [Touch, zadanie](../msbuild/touch-task.md)  
 Ustawia czas dostępu i modyfikacji plików.  
  
 [UnregisterAssembly, zadanie](../msbuild/unregisterassembly-task.md)  
 Wyrejestrowuje określonych zestawów do celów międzyoperacyjności COM.  
  
 [UpdateManifest, zadanie](../msbuild/updatemanifest-task.md)  
 Aktualizuje właściwości wybranego w manifeście i rezygnuje.  
  
 [Vbc, zadanie](../msbuild/vbc-task.md)  
 Wywołuje kompilator języka Visual Basic generuje pliki wykonywalne, bibliotek dołączanych dynamicznie lub modułów kodu...  
  
 [Warning, zadanie](../msbuild/warning-task.md)  
 Dzienniki ostrzeżenie podczas kompilacji w oparciu ocenianą instrukcji warunkowej.  
  
 [WriteCodeFragment, zadanie](../msbuild/writecodefragment-task.md)  
 Generuje plik tymczasowy kod, za pomocą fragmentu określonego wygenerowanego kodu. Nie powoduje usunięcia pliku.  
  
 [WriteLinesToFile, zadanie](../msbuild/writelinestofile-task.md)  
 Zapisuje określone elementy do pliku określony tekst.  
  
 [XmlPeek, zadanie](../msbuild/xmlpeek-task.md)  
 Zwraca wartości określonych przez zapytanie XPath z pliku XML.  
  
 [XmlPoke, zadanie](../msbuild/xmlpoke-task.md)  
 Ustawia wartości określonych przez zapytanie XPath do pliku XML.  
  
 [XslTransformation, zadanie](../msbuild/xsltransformation-task.md)  
 Przekształca dane wejściowe XML przy użyciu *Extensible arkusza stylów języka przekształcenia* (XSLT) lub obliczonych XSLT i dane wyjściowe do wyjścia urządzenia lub pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Wpisywanie zadania](../msbuild/task-writing.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
