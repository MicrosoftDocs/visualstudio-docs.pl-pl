---
title: Zadanie MT | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (C++), MT task
- MT task (MSBuild (C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe0ce106fc471431d3aac088eb3f45cfb28c564
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633060"
---
# <a name="mt-task"></a>MT — Zadanie

Zawija narzędzie Microsoft Manifest Tool, *mt.exe*. Aby uzyskać więcej informacji, zobacz [Mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **MT.** Większość parametrów zadania i kilka zestawów parametrów odpowiada opcji wiersza polecenia.

> [!NOTE]
> W dokumentacji *mt.exe* użyto**-** łącznika ( ) jako prefiksu dla opcji wiersza polecenia, ale w tym temacie użyto ukośnika (**/**). Każdy prefiks jest dopuszczalny.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalManifestFiles**|Parametr **Opcjonalny ciąg[].**<br /><br /> Określa nazwę jednego lub więcej plików manifestu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/manifest** opcji w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Dodatkoweopcje**|Opcjonalny parametr **String.**<br /><br /> Lista opcji wiersza polecenia. Na przykład\</ option1>\</ option2\<> / option#>. Ten parametr służy do określania opcji wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania **MT.**<br /><br /> Aby uzyskać więcej informacji, zobacz [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Assemblyidentity**|Opcjonalny parametr **String.**<br /><br /> Określa wartości atrybutów **zestawuIdentycyjność** elementu manifestu. Określ listę rozdzielanych przecinkami, gdzie pierwszym `name` składnikiem jest wartość atrybutu, a następnie jedna lub więcej par nazw/wartości, które mają formularz, * \<nazwę atrybutu>=<attribute_value>*.<br /><br /> Aby uzyskać więcej informacji, zobacz **/identity** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Nazwa pliku komponentu**|Opcjonalny parametr **String.**<br /><br /> Określa nazwę biblioteki łączy dynamicznych, którą zamierzasz utworzyć z plików *.rgs* lub *.tlb.* Ten parametr jest wymagany, jeśli określono parametry zadania **RegistrarScriptFile** lub **TypeLibraryFile** MT.<br /><br /> Aby uzyskać więcej informacji, zobacz **/dll** opcja w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Plik informacji o zależnościach**|Opcjonalny parametr **String.**<br /><br /> Określa plik informacji o zależności używany przez program Visual Studio do śledzenia informacji o zależności kompilacji dla narzędzia manifestu.|
|**BedManifest**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`plik manifestu osadza się w zestawie. Jeśli `false`, tworzy jako samodzielny plik manifestu.|
|**WłączdPIAwareness**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, dodaje do manifestu informacji, które oznacza aplikację jako DPI-aware. Pisanie aplikacji obsługującej dpi sprawia, że interfejs użytkownika wygląda konsekwentnie dobrze w wielu różnych ustawieniach wyświetlania o wysokiej rozdzielczości DPI.<br /><br /> Aby uzyskać więcej informacji, zobacz [Wysoka rozdzielczość DPI](/windows/desktop/win7devguide/high-dpi).|
|**Generowanie plikówCatalog**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`pliki definicji katalogu (*.cdf*) generuje.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/makecdfs** w [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Generowanie znaczników kategorii**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`powoduje wygenerowanie tagów kategorii. Jeśli ten `true`parametr jest , należy również określić parametr zadania **ManifestFromManagedAssemblyMT.**<br /><br /> Aby uzyskać więcej informacji, zobacz **/category** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Opcjonalny parametr **String.**<br /><br /> Wprowadź manifest z zasobu typu RT_MANIFEST, który ma określony identyfikator. Określ zasób \<formularza, plik>[;[ #]\<resource_id>], gdzie parametr> \<resource_id opcjonalny jest liczbą nieujemną, 16-bitową.<br /><br /> Jeśli `resource_id` nie zostanie określony, używana jest CREATEPROCESS_MANIFEST_RESOURCE wartość domyślna (1).<br /><br /> Aby uzyskać więcej informacji, zobacz **/inputresource** opcja w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestFromManagedAssembly**|Opcjonalny parametr **String.**<br /><br /> Generuje manifest z określonego zestawu zarządzanego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/managedassemblyname** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestToIgnore**|Opcjonalny parametr **String.**<br /><br /> (Nieużyno).|
|**Plik OutputManifest**|Opcjonalny parametr **String.**<br /><br /> Określa nazwę manifestu wyjściowego. Jeśli ten parametr zostanie pominięty i tylko jeden manifest jest obsługiwany na, manifest ten jest modyfikowany w miejscu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/out** opcja w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Dane wyjścioweManifestysy**|Opcjonalny parametr **String.**<br /><br /> Dane wyjściowe manifestu do zasobu typu RT_MANIFEST, który ma określony identyfikator. Zasób jest w \<formularzu, pliku>[;[ #]\<resource_id>], gdzie parametr> \<resource_id opcjonalny jest liczbą nieujemną, 16-bitową.<br /><br /> Jeśli `resource_id` nie zostanie określony, używana jest CREATEPROCESS_MANIFEST_RESOURCE wartość domyślna (1).<br /><br /> Aby uzyskać więcej informacji, zobacz **/outputresource** opcja w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**RegistrarScriptFile**|Opcjonalny parametr **String.**<br /><br /> Określa nazwę pliku skryptu rejestratora (*.rgs*) do użycia do obsługi manifestu COM bez rejestracji.<br /><br /> Aby uzyskać więcej informacji, zobacz **/rgs** opcja w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ReplacementsFile (Plik wymiany)**|Opcjonalny parametr **String.**<br /><br /> Określa plik zawierający wartości wymiennych ciągów w pliku skryptu rejestratora (*.rgs*).<br /><br /> Aby uzyskać więcej informacji, zobacz **/replacements** option w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Nazwa pliku ResourceOutputFile**|Opcjonalny parametr **String.**<br /><br /> Określa plik zasobów wyjściowych używany do osadzania manifestu w danych wyjściowych projektu.|
|**Źródeł**|Parametr `ITaskItem[]` opcjonalny.<br /><br /> Określa listę plików źródłowych manifestu oddzielonych spacjami.<br /><br /> Aby uzyskać więcej informacji, zobacz **/manifest** opcji w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**PomijanieDependencyElement**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, generuje manifest bez elementów zależności. Jeśli ten `true`parametr jest , należy również określić Parametr zadania **ManifestFromManagedAssemblyMT.**<br /><br /> Aby uzyskać więcej informacji, zobacz **/nodependency** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressStartupBanner (SuppressStartupBanner)**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program Zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji po uruchomieniu zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcja w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**TrackerLogDirectory (TrackerLogDirectory)**|Parametr `String` opcjonalny.<br /><br /> Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.|
|**TypLibraryFile**|Opcjonalny parametr **String.**<br /><br /> Określa nazwę pliku biblioteki typów (*tlb).* Jeśli określisz ten parametr, należy również określić parametr zadania **ComponentFileNameMT.**<br /><br /> Aby uzyskać więcej informacji, zobacz **/tlb** opcja w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AktualizacjaFileHashes**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, oblicza wartość mieszania plików w ścieżce określonej przez **UpdateFileHashesSearchPathMT** parametr zadania, a następnie aktualizuje wartość atrybutu **skrótu** elementu **pliku** manifestu przy użyciu obliczonej wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz **/hashupdate** opcja w [Mt.exe](/windows/desktop/SbsCs/mt-exe). Zobacz także **UpdateFileHashesSearchPath** parametr w tej tabeli.|
|**UpdateFileHashesSearchPath**|Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę wyszukiwania, która ma być używana podczas aktualizowanania skrótów plików. Ten parametr należy używać z parametrem zadania **UpdateFileHashesMT.**<br /><br /> Aby uzyskać więcej informacji, zobacz **UpdateFileHashes** parametr w tej tabeli.|
|**VerboseOutput (VerboseOutput)**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program wyświetla pełne informacje debugowania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/verbose** opcja w [Mt.exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
