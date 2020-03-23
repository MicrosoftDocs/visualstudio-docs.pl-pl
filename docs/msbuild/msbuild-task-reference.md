---
title: Odwołanie do zadania MSBuild | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbec3c7c020bae0e94bc16bdb1fe9740a36a93ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865326"
---
# <a name="msbuild-task-reference"></a>Odwołanie do zadania MSBuild

Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Zadania na poniższej liście są dołączone do MSBuild. Po zainstalowaniu obciążenia języka C++ dostępne są dodatkowe zadania, które są używane do tworzenia projektów języka C++. Aby uzyskać więcej informacji, zobacz [Zadania języka C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Oprócz parametrów wymienionych w tematach w tej sekcji, każde zadanie ma również następujące parametry:

| Parametr | Opis |
|-------------------| - |
| `Condition` | Parametr `String` opcjonalny.<br /><br /> Wyrażenie `Boolean` używane przez aparat MSBuild do określenia, czy to zadanie zostanie wykonane. Aby uzyskać informacje na temat warunków obsługiwanych przez MSBuild, zobacz [Warunki](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndKontynuuj** lub **prawda**. Gdy zadanie nie powiedzie się, kolejne zadania w [target](../msbuild/target-element-msbuild.md) element i kompilacji nadal wykonywać, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue**. Gdy zadanie nie powiedzie `Target` się, kolejne zadania w elemencie i kompilacji nadal wykonywać, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (domyślnie). Gdy zadanie zakończy się niepowodzeniem, pozostałe zadania w `Target` elemencie `Target` i kompilacji nie są wykonywane, a cały element i kompilacja jest uważany za nie powiodło się.<br /><br /> Wersje programu .NET Framework przed 4.5 `true` `false` obsługiwane tylko i wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [Jak: Ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>W tej sekcji

- [Klasa podstawowa zadania](../msbuild/task-base-class.md)

 Dodaje kilka parametrów do zadań, <xref:Microsoft.Build.Utilities.Task> które wynikają z klasy. Nie przeznaczone do bezpośredniego użycia.

- [Klasa podstawowa TaskExtension](../msbuild/taskextension-base-class.md)

 Dodaje kilka parametrów do zadań, <xref:Microsoft.Build.Tasks.TaskExtension> które wynikają z klasy. Nie przeznaczone do bezpośredniego użycia.

- [Klasa podstawowa ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Dodaje kilka parametrów do zadań, <xref:Microsoft.Build.Tasks.ToolTaskExtension> które wynikają z klasy. Nie przeznaczone do bezpośredniego użycia.

- [AL (Łącznik zespołu) zadanie](../msbuild/al-assembly-linker-task.md)

 Tworzy zestaw z manifestem z jednego lub więcej plików, które są modułami lub plikami zasobów.

- [AspNetCompiler zadanie](../msbuild/aspnetcompiler-task.md)

 *Zawija aspnet_compiler.exe*, narzędzie do wstępnej kompilacji aplikacji ASP.NET.

- [Zadanie Przypisywanie kultury](../msbuild/assignculture-task.md)

 Przypisuje identyfikatory kultury do elementów.

- [Zadanie konfiguracji assignproject](../msbuild/assignprojectconfiguration-task.md)

 Akceptuje listę ciągów konfiguracji i przypisuje je do określonych projektów.

- [Zadanie Przypisz ścieżkę docelową](../msbuild/assigntargetpath-task.md)

 Akceptuje listę plików i `<TargetPath>` dodaje atrybuty, jeśli nie są jeszcze określone.

- [Zadanie CallTarget](../msbuild/calltarget-task.md)

 Wywołuje obiekt docelowy w pliku projektu.

- [CombinePath zadanie](../msbuild/combinepath-task.md)

 Łączy określone ścieżki w jedną ścieżkę.

- [Zadanie ConvertToAbsolutePath](../msbuild/converttoabsolutepath-task.md)

 Konwertuje ścieżkę względną lub odwołanie na ścieżkę bezwzględną.

- [Kopiuj zadanie](../msbuild/copy-task.md)

 Kopiuje pliki do nowej lokalizacji.

- [Tworzenie zadania CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md)

 Tworzy nazwę manifestu w stylu C#z podanej nazwy pliku *resx* lub innego zasobu.

- [Zadanie CreateItem](../msbuild/createitem-task.md)

 Wypełnia kolekcje towarów z elementów wejściowych, umożliwiając kopiowanie elementów z jednej listy do drugiej.

- [CreateProperty — zadanie](../msbuild/createproperty-task.md)

 Wypełnia właściwości z wartości wejściowych, umożliwiając wartości do skopiowania z jednej właściwości lub ciągu do innej.

- [Utwórz zadanie CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Tworzy nazwę manifestu w stylu języka Visual Basic z podanej nazwy pliku *resx* lub innego zasobu.

- [Zadanie csc](../msbuild/csc-task.md)

 Wywołuje kompilator visual c# do tworzenia plików wykonywalnych, bibliotek łączy dynamicznych lub modułów kodu.

- [Usuwanie zadania](../msbuild/delete-task.md)

 Usuwa określone pliki.

- [Zadanie DownloadFile](../msbuild/downloadfile-task.md)

 Pobiera plik do określonej lokalizacji.

- [Zadanie błędu](../msbuild/error-task.md)

 Zatrzymuje kompilacji i rejestruje błąd na podstawie ocenione instrukcji warunkowej.

- [Zadanie Exec](../msbuild/exec-task.md)

 Uruchamia określony program lub polecenie z określonymi argumentami.

- [Zadanie Znajdź PlikAppConfigFile](../msbuild/findappconfigfile-task.md)

 Znajduje plik *app.config,* jeśli istnieje, na podanych listach.

- [Zadanie Znajdź Pozycję Na liście](../msbuild/findinlist-task.md)

 Znajduje element na określonej liście, który ma pasujące itemspec.

- [Zadanie Znajdź Ścieżkę](../msbuild/findunderpath-task.md)

 Określa, które elementy w określonej kolekcji elementów istnieją w określonym folderze i wszystkich jego podfolderach.

- [Zadanie FormatUrl](../msbuild/formaturl-task.md)

 Konwertuje adres URL na poprawny format adresu URL.

- [Zadanie FormatVersion](../msbuild/formatversion-task.md)

 Dołącza numer poprawki do numeru wersji.

- [Generowanie zadania Generowaniazarządzaj](../msbuild/generateapplicationmanifest-task.md)

 Generuje manifest aplikacji ClickOnce lub manifest macierzysty.

- [Generowanie zadania zdrobnienia](../msbuild/generatebootstrapper-task.md)

 Zapewnia zautomatyzowany sposób wykrywania, pobierania i instalowania aplikacji i jej wymagań wstępnych.

- [GenerateDeploymentManifest zadanie](../msbuild/generatedeploymentmanifest-task.md)

 Generuje manifest wdrożenia ClickOnce.

- [Zadanie GenerateResource](../msbuild/generateresource-task.md)

 Konwertuje pliki *.txt* i *.resx* na pliki binarne *.resources* w języku common language runtime.

- [Generowanie zadaniaTrustInfo](../msbuild/generatetrustinfo-task.md)

 Generuje zaufanie aplikacji z manifestu podstawowego `TargetZone` `ExcludedPermissions` oraz z i parametrów.

- [GetAssemblyDyto zadanie](../msbuild/getassemblyidentity-task.md)

 Pobiera tożsamości zestawu z określonych plików i wyprowadza informacje o tożsamości.

- [GetFileHash zadanie](../msbuild/getfilehash-task.md)

 Oblicza sumy kontrolne zawartości pliku lub zestawu plików.

- [Zadanie GetFrameworkPath](../msbuild/getframeworkpath-task.md)

 Pobiera ścieżkę do zestawów .NET Framework.

- [Zadanie GetFrameworkSdkPath](../msbuild/getframeworksdkpath-task.md)

 Pobiera ścieżkę do zestawu Windows Software Development Kit (SDK).

- [Zadanie GetReferenceAssemblyPaths](../msbuild/getreferenceassemblypaths-task.md)

 Zwraca ścieżki zestawu odwołań różnych struktur.

- [Zadanie LC](../msbuild/lc-task.md)

 Generuje plik *.license* z pliku *.licx.*

- [Zadanie MakeDir](../msbuild/makedir-task.md)

 Tworzy katalogi i, jeśli to konieczne, katalogi nadrzędne.

- [Zadanie wiadomości](../msbuild/message-task.md)

 Rejestruje komunikat podczas kompilacji.

- [Przenieś zadanie](../msbuild/move-task.md)

 Przenosi pliki w nową lokalizację.

- [Zadanie MSBuild](../msbuild/msbuild-task.md)

 Tworzy projekty MSBuild z innego projektu MSBuild.

- [ReadLinesFromFile zadanie](../msbuild/readlinesfromfile-task.md)

 Odczytuje listę elementów z pliku tekstowego.

- [Zarejestruj zadanie rejestrujasnajednak](../msbuild/registerassembly-task.md)

 Odczytuje metadane w określonym zestawie i dodaje niezbędne wpisy do rejestru.

- [RemoveDir zadanie](../msbuild/removedir-task.md)

 Usuwa określone katalogi i wszystkie jego pliki i podkatalogi.

- [Zadanie RemoveDuplicates](../msbuild/removeduplicates-task.md)

 Usuwa zduplikowane elementy z określonej kolekcji towarów.

- [Zadanie requiresFramework35SP1asześcijanie](../msbuild/requiresframework35sp1assembly-task.md)

 Określa, czy aplikacja wymaga dodatku SP1 .NET Framework 3.5.

- Zadanie ResGen

 Nieaktualne. Zadanie [GenerateResource](../msbuild/generateresource-task.md) służy do konwertowania plików *.txt* i *.resx* na pliki binarne *.resources* w języku ..

- [Zadanie ResolveAssemblyReference](../msbuild/resolveassemblyreference-task.md)

 Określa wszystkie zestawy, które zależą od określonych zestawów.

- [Zadanie ResolveComReference](../msbuild/resolvecomreference-task.md)

 Pobiera listę co najmniej jednej nazwy biblioteki typów lub plików *.tlb* i rozpoznaje te biblioteki typów do lokalizacji na dysku.

- [Zadanie ResolveKeySource](../msbuild/resolvekeysource-task.md)

 Określa źródło klucza silnej nazwy

- [ResolveManifestFiles zadanie](../msbuild/resolvemanifestfiles-task.md)

 Rozwiązuje następujące elementy w procesie kompilacji do plików do generowania manifestu: elementy utworzone, zależności, satelity, zawartość, symbole debugowania i dokumentacji.

- [Zadanie ResolveNativeReference](../msbuild/resolvenativereference-task.md)

 Rozpoznaje odwołania natywne.

- [ResolveNonMSBuildProjectOutput zadanie](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Określa pliki wyjściowe dla odwołań do projektu innych niż MSBuild.

- [Zadanie SGen](../msbuild/sgen-task.md)

 Tworzy zestaw serializacji XML dla typów w określonym zestawie.

- [SignFile zadanie](../msbuild/signfile-task.md)

 Podpisuje określony plik przy użyciu określonego certyfikatu.

- [Zadanie dotykowe](../msbuild/touch-task.md)

 Ustawia czasy dostępu i modyfikacji plików.

- [Zadanie wyrejestrowy assembly](../msbuild/unregisterassembly-task.md)

 Wyrejestrowanie określonych zestawów do celów współdziałanych COM.

- [Rozpakuj zadanie](../msbuild/unzip-task.md)

 Rozpakowywać archiwum *.zip* do określonej lokalizacji.

- [Zadanie UpdateManifest](../msbuild/updatemanifest-task.md)

 Aktualizuje wybrane właściwości w manifeście i rezygnuje.

- [Zadanie Vbc](../msbuild/vbc-task.md)

 Wywołuje kompilator języka Visual Basic do tworzenia plików wykonywalnych, bibliotek łączy dynamicznych lub modułów kodu..

- [VerifyFileHash zadanie](../msbuild/verifyfilehash-task.md)

 Sprawdza, czy plik pasuje do oczekiwanego skrótu pliku.

- [Warning — Zadanie](../msbuild/warning-task.md)

 Rejestruje ostrzeżenie podczas kompilacji na podstawie ocenianej instrukcji warunkowej.

- [Zadanie WriteCodeFragment](../msbuild/writecodefragment-task.md)

 Generuje tymczasowy plik kodu przy użyciu określonego wygenerowanego fragmentu kodu. Nie usuwa pliku.

- [Zadanie WriteLinesToFile](../msbuild/writelinestofile-task.md)

 Zapisuje określone elementy do określonego pliku tekstowego.

- [XmlPeek zadanie](../msbuild/xmlpeek-task.md)

 Zwraca wartości określone przez kwerendę XPath z pliku XML.

- [Zadanie XmlPoke](../msbuild/xmlpoke-task.md)

 Ustawia wartości określone przez kwerendę XPath w pliku XML.

- [Zadanie XslTransformation](../msbuild/xsltransformation-task.md)

 Przekształca dane wejściowe XML przy użyciu *transformacji języka arkusza stylów rozszerzalnych* (XSLT) lub skompilowanego XSLT i wyprowadza do urządzenia wyjściowego lub pliku.

- [Zadanie ZipDirectory](../msbuild/zipdirectory-task.md)

 Tworzy archiwum *zip* z zawartości katalogu.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Pisanie zadań](../msbuild/task-writing.md)
- [Zadania](../msbuild/msbuild-tasks.md)
