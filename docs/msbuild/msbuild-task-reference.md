---
title: Odwołanie do zadania programu MSBuild | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00af44212dd142dd94629f886a50b9646488af3b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747272"
---
# <a name="msbuild-task-reference"></a>Odwołanie do zadania programu MSBuild

Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Zadania z poniższej listy są dołączone do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Po zainstalowaniu [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] są dostępne dodatkowe zadania, które służą do kompilowania [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów. Aby uzyskać więcej informacji, zobacz [ C++ zadania](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Oprócz parametrów wymienionych w tematach w tej sekcji każde zadanie ma również następujące parametry:

| Parametr | Opis |
|-------------------| - |
| `Condition` | Opcjonalny parametr `String`.<br /><br /> Wyrażenie `Boolean` używane przez aparat [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do określenia, czy zadanie zostanie wykonane. Aby uzyskać informacje na temat warunków, które są obsługiwane przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], zobacz [warunki](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Opcjonalny parametr. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Gdy zadanie się nie powiedzie, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i Build są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue**. Gdy zadanie nie powiedzie się, kolejne zadania w elemencie `Target` i kompilacja nadal będą wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (wartość domyślna). Gdy zadanie nie powiedzie się, pozostałe zadania w elemencie `Target` i kompilacja nie są wykonywane, a cały element `Target` i kompilacja są uznawane za niepowodzenie.<br /><br /> Wersje .NET Framework przed 4,5 są obsługiwane tylko przez wartości `true` i `false`.<br /><br /> Aby uzyskać więcej informacji, zobacz [How to: ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>W tej sekcji

- [Klasa bazowa zadania](../msbuild/task-base-class.md)

 Dodaje kilka parametrów do zadań, które pochodzą z klasy <xref:Microsoft.Build.Utilities.Task>.

- [Klasa bazowa TaskExtension](../msbuild/taskextension-base-class.md)

 Dodaje kilka parametrów do zadań, które pochodzą z klasy <xref:Microsoft.Build.Tasks.TaskExtension>.

- [Klasa bazowa ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Dodaje kilka parametrów do zadań, które pochodzą z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension>.

- [AL (Konsolidator zestawu) — zadanie](../msbuild/al-assembly-linker-task.md)

 Tworzy zestaw z manifestem z co najmniej jednego pliku, który jest modułem lub plikami zasobów.

- [AspNetCompiler —, zadanie](../msbuild/aspnetcompiler-task.md)

 Zawija *aspnet_compiler. exe*, narzędzie do prekompilowania aplikacji ASP.NET.

- [AssignCulture —, zadanie](../msbuild/assignculture-task.md)

 Przypisuje identyfikatory kultur do elementów.

- [AssignProjectConfiguration, zadanie](../msbuild/assignprojectconfiguration-task.md)

 Akceptuje listę ciągów konfiguracji i przypisuje je do określonych projektów.

- [AssignTargetPath, zadanie](../msbuild/assigntargetpath-task.md)

 Akceptuje listę plików i dodaje atrybuty `<TargetPath>`, jeśli nie zostały one jeszcze określone.

- [CallTarget —, zadanie](../msbuild/calltarget-task.md)

 Wywołuje obiekt docelowy w pliku projektu.

- [CombinePath —, zadanie](../msbuild/combinepath-task.md)

 Łączy określone ścieżki w jedną ścieżkę.

- [ConvertToAbsolutePath —, zadanie](../msbuild/converttoabsolutepath-task.md)

 Konwertuje ścieżkę względną lub odwołanie na ścieżkę bezwzględną.

- [Kopiuj zadanie](../msbuild/copy-task.md)

 Kopiuje pliki do nowej lokalizacji.

- [CreateCSharpManifestResourceName —, zadanie](../msbuild/createcsharpmanifestresourcename-task.md)

 Tworzy nazwę manifestu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]w stylu na podstawie danej nazwy pliku *resx* lub innego zasobu.

- [Zadanie elementu](../msbuild/createitem-task.md)

 Wypełnia kolekcje elementów z elementów wejściowych, umożliwiając kopiowanie elementów z jednej listy do innej.

- [Zadanie właściwości](../msbuild/createproperty-task.md)

 Wypełnia właściwości z wartości wejściowych, umożliwiając kopiowanie wartości z jednej właściwości lub ciągu do innej.

- [CreateVisualBasicManifestResourceName —, zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Tworzy nazwę manifestu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]w stylu na podstawie danej nazwy pliku *resx* lub innego zasobu.

- [CSC — zadanie](../msbuild/csc-task.md)

 Wywołuje kompilator wizualny C# do tworzenia plików wykonywalnych, bibliotek dołączanych dynamicznie lub modułów kodu.

- [Usuń zadanie](../msbuild/delete-task.md)

 Usuwa określone pliki.

- [DownloadFile, zadanie](../msbuild/downloadfile-task.md)

 Pobiera plik do określonej lokalizacji.

- [Error — zadanie](../msbuild/error-task.md)

 Kończy kompilację i rejestruje błąd na podstawie ocenianej instrukcji warunkowej.

- [Exec — zadanie](../msbuild/exec-task.md)

 Uruchamia określony program lub polecenie z określonymi argumentami.

- [FindAppConfigFile —, zadanie](../msbuild/findappconfigfile-task.md)

 Znajduje plik *App. config* (jeśli istnieje) na dostarczonych listach.

- [FindInList —, zadanie](../msbuild/findinlist-task.md)

 Znajduje element na określonej liście, który ma pasującą specyfikacja_elementu.

- [FindUnderPath —, zadanie](../msbuild/findunderpath-task.md)

 Określa, które elementy w określonej kolekcji elementów istnieją w określonym folderze i wszystkich jego podfolderach.

- [FormatUrl —, zadanie](../msbuild/formaturl-task.md)

 Konwertuje adres URL na prawidłowy format adresu URL.

- [FormatVersion, zadanie](../msbuild/formatversion-task.md)

 Dołącza numer poprawki do numeru wersji.

- [GenerateApplicationManifest —, zadanie](../msbuild/generateapplicationmanifest-task.md)

 Generuje manifest aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lub natywny manifest.

- [GenerateBootstrapper —, zadanie](../msbuild/generatebootstrapper-task.md)

 Zapewnia zautomatyzowany sposób wykrywania, pobierania i instalowania aplikacji oraz jej wymagań wstępnych.

- [GenerateDeploymentManifest —, zadanie](../msbuild/generatedeploymentmanifest-task.md)

 Generuje manifest wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

- [GenerateResource, zadanie](../msbuild/generateresource-task.md)

 Konwertuje pliki *txt* i *resx* na *pliki binarne plików* binarnych środowiska uruchomieniowego języka wspólnego.

- [GenerateTrustInfo —, zadanie](../msbuild/generatetrustinfo-task.md)

 Generuje zaufanie aplikacji z manifestu podstawowego oraz z parametrów `TargetZone` i `ExcludedPermissions`.

- [GetAssemblyIdentity —, zadanie](../msbuild/getassemblyidentity-task.md)

 Pobiera tożsamości zestawu z określonych plików i wyświetla informacje o tożsamości.

- [GetFileHash, zadanie](../msbuild/getfilehash-task.md)

 Oblicza sumy kontrolne zawartości pliku lub zestawu plików.

- [GetFrameworkPath —, zadanie](../msbuild/getframeworkpath-task.md)

 Pobiera ścieżkę do zestawów .NET Framework.

- [GetFrameworkSdkPath —, zadanie](../msbuild/getframeworksdkpath-task.md)

 Pobiera ścieżkę do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].

- [GetReferenceAssemblyPaths, zadanie](../msbuild/getreferenceassemblypaths-task.md)

 Zwraca ścieżki zestawów referencyjnych różnych struktur.

- [LC — zadanie](../msbuild/lc-task.md)

 Generuje plik *licencji* z pliku *. licx* .

- [MakeDir, zadanie](../msbuild/makedir-task.md)

 Tworzy katalogi i, w razie potrzeby, wszystkie katalogi nadrzędne.

- [Komunikat — zadanie](../msbuild/message-task.md)

 Rejestruje komunikat w trakcie kompilacji.

- [Przenieś zadanie](../msbuild/move-task.md)

 Przenosi pliki do nowej lokalizacji.

- [Zadanie MSBuild](../msbuild/msbuild-task.md)

 Kompiluje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty z innego projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

- [ReadLinesFromFile —, zadanie](../msbuild/readlinesfromfile-task.md)

 Odczytuje listę elementów z pliku tekstowego.

- [RegisterAssembly —, zadanie](../msbuild/registerassembly-task.md)

 Odczytuje metadane w określonym zestawie i dodaje niezbędne wpisy do rejestru.

- [RemoveDir —, zadanie](../msbuild/removedir-task.md)

 Usuwa określone katalogi i wszystkie jego pliki i podkatalogi.

- [RemoveDuplicates —, zadanie](../msbuild/removeduplicates-task.md)

 Usuwa zduplikowane elementy z określonej kolekcji elementów.

- [Requiresframework35sp1assembly —, zadanie](../msbuild/requiresframework35sp1assembly-task.md)

 Określa, czy aplikacja wymaga .NET Framework 3,5 z dodatkiem SP1.

- ResGen, zadanie

 Nieaktualne. Zadanie [GenerateResource](../msbuild/generateresource-task.md) służy do konwertowania plików *txt* i *resx* do i z plików binarnych pliku binarnego środowiska uruchomieniowego języka *wspólnego.*

- [ResolveAssemblyReference —, zadanie](../msbuild/resolveassemblyreference-task.md)

 Określa wszystkie zestawy, które są zależne od określonych zestawów.

- [ResolveComReference —, zadanie](../msbuild/resolvecomreference-task.md)

 Przyjmuje listę jednej lub więcej nazw bibliotek typów lub plików *TLB* i rozpoznaje te biblioteki typów do lokalizacji na dysku.

- [ResolveKeySource —, zadanie](../msbuild/resolvekeysource-task.md)

 Określa źródło klucza o silnej nazwie

- [ResolveManifestFiles —, zadanie](../msbuild/resolvemanifestfiles-task.md)

 Rozwiązuje następujące elementy w procesie kompilacji do plików na potrzeby generowania manifestu: skompilowane elementy, zależności, satelity, zawartość, symbole debugowania i dokumentacja.

- [ResolveNativeReference —, zadanie](../msbuild/resolvenativereference-task.md)

 Rozwiązuje odwołania natywne.

- [ResolveNonMSBuildProjectOutput —, zadanie](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Określa pliki wyjściowe dla odwołań projektu innych niż MSBuild.

- [SGen, zadanie](../msbuild/sgen-task.md)

 Tworzy zestaw serializacji XML dla typów w określonym zestawie.

- [SignFile —, zadanie](../msbuild/signfile-task.md)

 Podpisuje określony plik przy użyciu podanego certyfikatu.

- [Dotknięcie zadania](../msbuild/touch-task.md)

 Ustawia czasy dostępu i modyfikacji plików.

- [UnregisterAssembly —, zadanie](../msbuild/unregisterassembly-task.md)

 Wyrejestrowuje określone zestawy na potrzeby współdziałania z modelem COM.

- [Rozpakuj zadanie](../msbuild/unzip-task.md)

 Rozpakuje Archiwum *. zip* do określonej lokalizacji.

- [UpdateManifest —, zadanie](../msbuild/updatemanifest-task.md)

 Aktualizuje wybrane właściwości w manifeście i podpisuje je.

- [VBC, zadanie](../msbuild/vbc-task.md)

 Wywołuje kompilator Visual Basic do tworzenia plików wykonywalnych, bibliotek dołączanych dynamicznie lub modułów kodu.

- [VerifyFileHash, zadanie](../msbuild/verifyfilehash-task.md)

 Sprawdza, czy plik jest zgodny z oczekiwanym skrótem pliku.

- [Ostrzeżenie — zadanie](../msbuild/warning-task.md)

 Rejestruje ostrzeżenie podczas kompilacji oparte na obliczanej instrukcji warunkowej.

- [WriteCodeFragment, zadanie](../msbuild/writecodefragment-task.md)

 Generuje tymczasowy plik kodu przy użyciu określonego wygenerowanego fragmentu kodu. Nie usuwa pliku.

- [WriteLinesToFile —, zadanie](../msbuild/writelinestofile-task.md)

 Zapisuje określone elementy do określonego pliku tekstowego.

- [XmlPeek — zadanie](../msbuild/xmlpeek-task.md)

 Zwraca wartości określone przez zapytanie XPath z pliku XML.

- [XmlPoke —, zadanie](../msbuild/xmlpoke-task.md)

 Ustawia wartości określone przez zapytanie XPath w pliku XML.

- [XslTransformation —, zadanie](../msbuild/xsltransformation-task.md)

 Przekształca dane wejściowe XML przy użyciu *Extensible Stylesheet Language Transformation* (XSLT) lub skompilowanego XSLT i wyjść do urządzenia wyjściowego lub pliku.

- [ZipDirectory, zadanie](../msbuild/zipdirectory-task.md)

 Tworzy archiwum *zip* z zawartości katalogu.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Pisanie zadania](../msbuild/task-writing.md)
- [Zadania](../msbuild/msbuild-tasks.md)