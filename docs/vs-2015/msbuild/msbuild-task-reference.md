---
title: Odwołanie do zadania programu MSBuild | Microsoft Docs
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
ms.openlocfilehash: 19fe581985ec173099790311517c0442a9c29c2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154105"
---
# <a name="msbuild-task-reference"></a>Odwołanie do zadania MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Zadania z poniższej listy są dołączone do programu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Po [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] zainstalowaniu programu są dostępne dodatkowe zadania, które są używane do kompilowania [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektów. Aby uzyskać więcej informacji, zobacz [Visual C++ Tasks](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Oprócz parametrów wymienionych w tematach w tej sekcji każde zadanie ma również następujące parametry:  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Condition`|Opcjonalny `String` parametr.<br /><br /> `Boolean`Wyrażenie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używane przez aparat do określenia, czy zadanie zostanie wykonane. Aby uzyskać informacje na temat warunków, które są obsługiwane przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] program, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Gdy zadanie się nie powiedzie, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i Build są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue**. Gdy zadanie nie powiedzie się, kolejne zadania w `Target` elemencie i kompilacja będą nadal wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (wartość domyślna). Jeśli zadanie nie powiedzie się, pozostałe zadania w `Target` elemencie i kompilacja nie są wykonywane, a cały `Target` element i kompilacja są uważane za zakończone niepowodzeniem.<br /><br /> Wersje .NET Framework przed 4,5 obsługiwane tylko `true` `false` wartości i.<br /><br /> Aby uzyskać więcej informacji, zobacz [How to: ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Klasa bazowa zadania](../msbuild/task-base-class.md)  
 Dodaje kilka parametrów do zadań, które pochodzą od <xref:Microsoft.Build.Utilities.Task> klasy.  
  
 [Klasa bazowa TaskExtension](../msbuild/taskextension-base-class.md)  
 Dodaje kilka parametrów do zadań, które pochodzą od <xref:Microsoft.Build.Tasks.TaskExtension> klasy.  
  
 [Klasa bazowa ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)  
 Dodaje kilka parametrów do zadań, które pochodzą od <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy.  
  
 [AL (Konsolidator zestawu) — zadanie](../msbuild/al-assembly-linker-task.md)  
 Tworzy zestaw z manifestem z co najmniej jednego pliku, który jest modułem lub plikami zasobów.  
  
 [AspNetCompiler —, zadanie](../msbuild/aspnetcompiler-task.md)  
 Zawija aspnet_compiler.exe, narzędzie do prekompilowania aplikacji ASP.NET.  
  
 [AssignCulture —, zadanie](../msbuild/assignculture-task.md)  
 Przypisuje identyfikatory kultur do elementów.  
  
 [AssignProjectConfiguration, zadanie](../msbuild/assignprojectconfiguration-task.md)  
 Akceptuje listę ciągów konfiguracji i przypisuje je do określonych projektów.  
  
 [AssignTargetPath, zadanie](../msbuild/assigntargetpath-task.md)  
 Akceptuje listę plików i dodaje atrybuty, `<TargetPath>` Jeśli nie zostały one jeszcze określone.  
  
 [CallTarget —, zadanie](../msbuild/calltarget-task.md)  
 Wywołuje obiekt docelowy w pliku projektu.  
  
 [CombinePath —, zadanie](../msbuild/combinepath-task.md)  
 Łączy określone ścieżki w jedną ścieżkę.  
  
 [ConvertToAbsolutePath —, zadanie](../msbuild/converttoabsolutepath-task.md)  
 Konwertuje ścieżkę względną lub odwołanie na ścieżkę bezwzględną.  
  
 [Kopiuj zadanie](../msbuild/copy-task.md)  
 Kopiuje pliki do nowej lokalizacji.  
  
 [CreateCSharpManifestResourceName —, zadanie](../msbuild/createcsharpmanifestresourcename-task.md)  
 Tworzy [!INCLUDE[csprcs](../includes/csprcs-md.md)] nazwę manifestu w stylu na podstawie danej nazwy pliku resx lub innego zasobu.  
  
 [Zadanie elementu](../msbuild/createitem-task.md)  
 Wypełnia kolekcje elementów z elementów wejściowych, umożliwiając kopiowanie elementów z jednej listy do innej.  
  
 [Zadanie właściwości](../msbuild/createproperty-task.md)  
 Wypełnia właściwości z wartości wejściowych, umożliwiając kopiowanie wartości z jednej właściwości lub ciągu do innej.  
  
 [CreateVisualBasicManifestResourceName —, zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Tworzy [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nazwę manifestu w stylu na podstawie danej nazwy pliku resx lub innego zasobu.  
  
 [CSC — zadanie](../msbuild/csc-task.md)  
 Wywołuje kompilator Visual C# do tworzenia plików wykonywalnych, bibliotek dołączanych dynamicznie lub modułów kodu.  
  
 [Usuń zadanie](../msbuild/delete-task.md)  
 Usuwa określone pliki.  
  
 [Error — zadanie](../msbuild/error-task.md)  
 Kończy kompilację i rejestruje błąd na podstawie ocenianej instrukcji warunkowej.  
  
 [Exec — zadanie](../msbuild/exec-task.md)  
 Uruchamia określony program lub polecenie z określonymi argumentami.  
  
 [FindAppConfigFile —, zadanie](../msbuild/findappconfigfile-task.md)  
 Znajduje plik app.config, jeśli istnieje, na określonych listach.  
  
 [FindInList —, zadanie](../msbuild/findinlist-task.md)  
 Znajduje element na określonej liście, który ma pasującą specyfikacja_elementu.  
  
 [FindUnderPath —, zadanie](../msbuild/findunderpath-task.md)  
 Określa, które elementy w określonej kolekcji elementów istnieją w określonym folderze i wszystkich jego podfolderach.  
  
 [FormatUrl —, zadanie](../msbuild/formaturl-task.md)  
 Konwertuje adres URL na prawidłowy format adresu URL.  
  
 [FormatVersion, zadanie](../msbuild/formatversion-task.md)  
 Dołącza numer poprawki do numeru wersji.  
  
 [GenerateApplicationManifest —, zadanie](../msbuild/generateapplicationmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikacji lub natywny manifest.  
  
 [GenerateBootstrapper —, zadanie](../msbuild/generatebootstrapper-task.md)  
 Zapewnia zautomatyzowany sposób wykrywania, pobierania i instalowania aplikacji oraz jej wymagań wstępnych.  
  
 [GenerateDeploymentManifest —, zadanie](../msbuild/generatedeploymentmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest wdrożenia.  
  
 [GenerateResource, zadanie](../msbuild/generateresource-task.md)  
 Konwertuje pliki txt i resx na pliki binarne plików binarnych środowiska uruchomieniowego języka wspólnego.  
  
 [GenerateTrustInfo —, zadanie](../msbuild/generatetrustinfo-task.md)  
 Generuje zaufanie aplikacji z manifestu podstawowego oraz z `TargetZone` `ExcludedPermissions` parametrów i.  
  
 [GetAssemblyIdentity —, zadanie](../msbuild/getassemblyidentity-task.md)  
 Pobiera tożsamości zestawu z określonych plików i wyświetla informacje o tożsamości.  
  
 [GetFrameworkPath —, zadanie](../msbuild/getframeworkpath-task.md)  
 Pobiera ścieżkę do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zestawów.  
  
 [GetFrameworkSdkPath —, zadanie](../msbuild/getframeworksdkpath-task.md)  
 Pobiera ścieżkę do [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] .  
  
 [GetReferenceAssemblyPaths, zadanie](../msbuild/getreferenceassemblypaths-task.md)  
 Zwraca ścieżki zestawów referencyjnych różnych struktur.  
  
 [LC — zadanie](../msbuild/lc-task.md)  
 Generuje plik licencji z pliku. licx.  
  
 [MakeDir, zadanie](../msbuild/makedir-task.md)  
 Tworzy katalogi i, w razie potrzeby, wszystkie katalogi nadrzędne.  
  
 [Komunikat — zadanie](../msbuild/message-task.md)  
 Rejestruje komunikat w trakcie kompilacji.  
  
 [Przenieś zadanie](../msbuild/move-task.md)  
 Przenosi pliki do nowej lokalizacji.  
  
 [Zadanie MSBuild](../msbuild/msbuild-task.md)  
 Kompiluje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekty z innego [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu.  
  
 [ReadLinesFromFile —, zadanie](../msbuild/readlinesfromfile-task.md)  
 Odczytuje listę elementów z pliku tekstowego.  
  
 [RegisterAssembly —, zadanie](../msbuild/registerassembly-task.md)  
 Odczytuje metadane w określonym zestawie i dodaje niezbędne wpisy do rejestru.  
  
 [RemoveDir —, zadanie](../msbuild/removedir-task.md)  
 Usuwa określone katalogi i wszystkie jego pliki i podkatalogi.  
  
 [RemoveDuplicates —, zadanie](../msbuild/removeduplicates-task.md)  
 Usuwa zduplikowane elementy z określonej kolekcji elementów.  
  
 [Requiresframework35sp1assembly —, zadanie](../msbuild/requiresframework35sp1assembly-task.md)  
 Określa, czy aplikacja wymaga .NET Framework 3,5 z dodatkiem SP1.  
  
 ResGen, zadanie  
 Nieaktualne. Zadanie [GenerateResource](../msbuild/generateresource-task.md) służy do konwertowania plików txt i resx do i z plików binarnych pliku binarnego środowiska uruchomieniowego języka wspólnego.  
  
 [ResolveAssemblyReference —, zadanie](../msbuild/resolveassemblyreference-task.md)  
 Określa wszystkie zestawy, które są zależne od określonych zestawów.  
  
 [ResolveComReference —, zadanie](../msbuild/resolvecomreference-task.md)  
 Przyjmuje listę jednej lub więcej nazw bibliotek typów lub plików TLB i rozpoznaje te biblioteki typów do lokalizacji na dysku.  
  
 [ResolveKeySource —, zadanie](../msbuild/resolvekeysource-task.md)  
 Określa źródło klucza o silnej nazwie  
  
 [ResolveManifestFiles —, zadanie](../msbuild/resolvemanifestfiles-task.md)  
 Rozwiązuje następujące elementy w procesie kompilacji do plików na potrzeby generowania manifestu: skompilowane elementy, zależności, satelity, zawartość, symbole debugowania i dokumentacja.  
  
 [ResolveNativeReference —, zadanie](../msbuild/resolvenativereference-task.md)  
 Rozwiązuje odwołania natywne.  
  
 [ResolveNonMSBuildProjectOutput —, zadanie](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Określa pliki wyjściowe dla odwołań projektu innych niż MSBuild.  
  
 [SGen, zadanie](../msbuild/sgen-task.md)  
 Tworzy zestaw serializacji XML dla typów w określonym zestawie.  
  
 [SignFile —, zadanie](../msbuild/signfile-task.md)  
 Podpisuje określony plik przy użyciu podanego certyfikatu.  
  
 [Dotknięcie zadania](../msbuild/touch-task.md)  
 Ustawia czasy dostępu i modyfikacji plików.  
  
 [UnregisterAssembly —, zadanie](../msbuild/unregisterassembly-task.md)  
 Wyrejestrowuje określone zestawy na potrzeby współdziałania z modelem COM.  
  
 [UpdateManifest —, zadanie](../msbuild/updatemanifest-task.md)  
 Aktualizuje wybrane właściwości w manifeście i podpisuje je.  
  
 [VBC, zadanie](../msbuild/vbc-task.md)  
 Wywołuje kompilator Visual Basic do tworzenia plików wykonywalnych, bibliotek dołączanych dynamicznie lub modułów kodu.  
  
 [Ostrzeżenie — zadanie](../msbuild/warning-task.md)  
 Rejestruje ostrzeżenie podczas kompilacji oparte na obliczanej instrukcji warunkowej.  
  
 [WriteCodeFragment, zadanie](../msbuild/writecodefragment-task.md)  
 Generuje tymczasowy plik kodu przy użyciu określonego wygenerowanego fragmentu kodu. Nie usuwa pliku.  
  
 [WriteLinesToFile —, zadanie](../msbuild/writelinestofile-task.md)  
 Zapisuje określone elementy do określonego pliku tekstowego.  
  
 [XmlPeek — zadanie](../msbuild/xmlpeek-task.md)  
 Zwraca wartości określone przez zapytanie XPath z pliku XML.  
  
 [XmlPoke —, zadanie](../msbuild/xmlpoke-task.md)  
 Ustawia wartości określone przez zapytanie XPath w pliku XML.  
  
 [XslTransformation —, zadanie](../msbuild/xsltransformation-task.md)  
 Przekształca dane wejściowe XML przy użyciu *Extensible Stylesheet Language Transformation* (XSLT) lub skompilowanego XSLT i wyjść do urządzenia wyjściowego lub pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Pisanie zadania](../msbuild/task-writing.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
