---
title: MT — zadanie | Microsoft Docs
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
ms.openlocfilehash: 2f90a1349771ab67f342a3490874cd422051cac2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595033"
---
# <a name="mt-task"></a>MT — Zadanie
Zawija narzędzie manifestu Microsoft, *Mt. exe*. Aby uzyskać więcej informacji, zobacz [Mt. exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry **MT** zadania. Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.

> [!NOTE]
> W dokumentacji programu *Mt. exe* jest stosowany łącznik ( **-** ) jako prefiks opcji wiersza polecenia, ale w tym temacie jest stosowany ukośnik ( **/** ). Dowolny prefiks jest akceptowalny.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalManifestFiles**|Opcjonalny parametr **String []** .<br /><br /> Określa nazwę jednego lub więcej plików manifestu.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/manifest** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji wiersza polecenia. Na przykład/\<opcja1 >/\<opcja2 >/\<opcji # >. Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr **MT** .<br /><br /> Aby uzyskać więcej informacji, zobacz [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|Opcjonalny parametr **ciągu** .<br /><br /> Określa wartości atrybutów elementu **assemblyIdentity** manifestu. Określ listę rozdzielaną przecinkami, w której pierwszy składnik jest wartością atrybutu `name`, po którym następuje co najmniej jedna para nazwa/wartość mająca postać, *\<nazwa atrybutu > = < attribute_value >* .<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/Identity** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ComponentFileName**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę biblioteki dołączanej dynamicznie, która ma zostać utworzona na podstawie plików *. RGS* lub *. tlb* . Ten parametr jest wymagany, jeśli określono parametry zadania **RegistrarScriptFile** lub **TypeLibraryFile** Mt.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/dll** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**DependencyInformationFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa plik informacji o zależnościach używany przez program Visual Studio do śledzenia informacji o zależnościach kompilacji dla narzędzia manifestu.|
|**EmbedManifest**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, osadzi plik manifestu w zestawie. Jeśli `false`, program tworzy jako autonomiczny plik manifestu.|
|**EnableDPIAwareness**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program dodaje do informacji manifestu, które oznaczają aplikację jako obsługującą ustawienia DPI. Pisanie aplikacji z obsługą rozdzielczości DPI sprawia, że interfejs użytkownika wygląda spójnie w wielu różnych ustawieniach wyświetlania o wysokiej rozdzielczości DPI.<br /><br /> Aby uzyskać więcej informacji, zobacz [wysokiej rozdzielczości DPI](/windows/desktop/win7devguide/high-dpi).|
|**GenerateCatalogFiles**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program generuje pliki definicji katalogu (*CDF*).<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/makecdfs** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**GenerateCategoryTags**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, powoduje generowanie tagów kategorii. Jeśli ten parametr jest `true`, należy również określić parametr zadania **ManifestFromManagedAssemblyMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/Category** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Opcjonalny parametr **ciągu** .<br /><br /> Wprowadź manifest z zasobu typu RT_MANIFEST o określonym identyfikatorze. Określ zasób formularza, \<> pliku [; [ #]\<resource_id >], gdzie opcjonalny \<resource_id > parametr jest liczbą nieujemną, 16-bitową.<br /><br /> Jeśli żadna `resource_id` nie zostanie określona, zostanie użyta wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/inputresource** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestFromManagedAssembly**|Opcjonalny parametr **ciągu** .<br /><br /> Generuje manifest z określonego zarządzanego zestawu.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/managedassemblyname** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestToIgnore**|Opcjonalny parametr **ciągu** .<br /><br /> (Nieużywane).|
|**OutputManifestFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę manifestu danych wyjściowych. Jeśli ten parametr zostanie pominięty i tylko jeden manifest jest obsługiwany na, ten manifest jest modyfikowany.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/out** w programie [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**OutputResourceManifests**|Opcjonalny parametr **ciągu** .<br /><br /> Dane wyjściowe manifestu do zasobu typu RT_MANIFEST o określonym identyfikatorze. Zasób ma postać, \<pliku > [; [ #]\<resource_id >], gdzie opcjonalny \<resource_id > parametr jest liczbą nieujemną, 16-bitową.<br /><br /> Jeśli żadna `resource_id` nie zostanie określona, zostanie użyta wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/outputresource** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**RegistrarScriptFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku skryptu rejestratora ( *. RGS*), który ma być używany do obsługi manifestu COM bez rejestracji.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/RGS** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ReplacementsFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa plik, który zawiera wartości dla wymiennych ciągów w pliku skryptu rejestratora ( *. RGS*).<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/replacements** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ResourceOutputFileName**|Opcjonalny parametr **ciągu** .<br /><br /> Określa plik zasobów wyjściowych służący do osadzenia manifestu w danych wyjściowych projektu.|
|**Źródeł**|Opcjonalny parametr `ITaskItem[]`.<br /><br /> Określa listę plików źródłowych manifestu rozdzielonych spacjami.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/manifest** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressDependencyElement**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, generuje manifest bez elementów zależności. Jeśli ten parametr jest `true`, należy również określić parametr zadania **ManifestFromManagedAssemblyMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/nodependency** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressStartupBanner**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/nologo** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**Katalog trackerlogdirectory**|Opcjonalny parametr `String`.<br /><br /> Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.|
|**TypeLibraryFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku biblioteki typów ( *. tlb*). W przypadku określenia tego parametru należy także określić parametr zadania **ComponentFileNameMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/TLB** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**UpdateFileHashes**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, oblicza wartość skrótu plików w ścieżce określonej przez parametr zadania **UpdateFileHashesSearchPathMT** , a następnie aktualizuje wartość atrybutu **hash** elementu **pliku** manifestu przy użyciu wartości obliczanej.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/hashupdate** w pliku [Mt. exe](/windows/desktop/SbsCs/mt-exe). Zobacz również parametr **UpdateFileHashesSearchPath** w tej tabeli.|
|**UpdateFileHashesSearchPath**|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę wyszukiwania do użycia podczas aktualizowania skrótów plików. Użyj tego parametru z parametrem zadania **UpdateFileHashesMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz **UpdateFileHashes** parametr w tej tabeli.|
|**VerboseOutput**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, wyświetla pełne informacje o debugowaniu.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/verbose** w programie [Mt. exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
