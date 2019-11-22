---
title: MT — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBUILD (Visual C++), MT task
- MT task (MSBuild (Visual C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc6fe1c581cfcc506eeb985b0b138edfab12112
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295544"
---
# <a name="mt-task"></a>MT — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija narzędzie manifestu Microsoft, Mt. exe. Aby uzyskać więcej informacji, zobacz "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **MT** zadania. Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.  
  
> [!NOTE]
> W dokumentacji programu Mt. exe jest stosowany łącznik ( **-** ) jako prefiks opcji wiersza polecenia, ale w tym temacie jest stosowany ukośnik ( **/** ). Dowolny prefiks jest akceptowalny.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Opcjonalny parametr **String []** .<br /><br /> Określa nazwę jednego lub więcej plików manifestu.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/manifest** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji wiersza polecenia. Na przykład " */option1/option2 Option #* ". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr **MT** .<br /><br /> Aby uzyskać więcej informacji, zobacz "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**AssemblyIdentity**|Opcjonalny parametr **ciągu** .<br /><br /> Określa wartości atrybutów elementu **assemblyIdentity** manifestu. Określ listę rozdzielaną przecinkami, w której pierwszy składnik jest wartością atrybutu `name`, po którym następuje co najmniej jedna para nazwa/wartość mająca postać, *\<nazwa atrybutu > = < attribute_value >* .<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/Identity** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**ComponentFileName**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę biblioteki dołączanej dynamicznie, która ma zostać utworzona na podstawie plików. RGS lub. tlb. Ten parametr jest wymagany, jeśli określono parametry zadania **RegistrarScriptFile** lub **TypeLibraryFile** Mt.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/dll** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**DependencyInformationFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa plik informacji o zależnościach używany przez program Visual Studio do śledzenia informacji o zależnościach kompilacji dla narzędzia manifestu.|  
|**EmbedManifest**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, osadzi plik manifestu w zestawie. Jeśli `false`, program tworzy jako autonomiczny plik manifestu.|  
|**EnableDPIAwareness**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program dodaje do informacji manifestu, które oznaczają aplikację jako obsługującą ustawienia DPI. Pisanie aplikacji z obsługą rozdzielczości DPI sprawia, że interfejs użytkownika wygląda spójnie w wielu różnych ustawieniach wyświetlania o wysokiej rozdzielczości DPI.<br /><br /> Aby uzyskać więcej informacji, zobacz "High DPI" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**GenerateCatalogFiles**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program generuje pliki definicji katalogu (CDF).<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/makecdfs** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**GenerateCategoryTags**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, powoduje generowanie tagów kategorii. Jeśli ten parametr jest `true`, należy również określić parametr zadania **ManifestFromManagedAssemblyMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/Category** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**InputResourceManifests**|Opcjonalny parametr **ciągu** .<br /><br /> Wprowadź manifest z zasobu typu RT_MANIFEST o określonym identyfikatorze. Określ zasób formularza, _\<> pliku [_ **;** _[_ **#** _] < resource_id >]_ , gdzie opcjonalny parametr `resource_id` jest liczbą nieujemną, 16-bitową.<br /><br /> Jeśli żadna `resource_id` nie zostanie określona, zostanie użyta wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/inputresource** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**ManifestFromManagedAssembly**|Opcjonalny parametr **ciągu** .<br /><br /> Generuje manifest z określonego zarządzanego zestawu.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/managedassemblyname** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**ManifestToIgnore**|Opcjonalny parametr **ciągu** .<br /><br /> (Nieużywane).|  
|**OutputManifestFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę manifestu danych wyjściowych. Jeśli ten parametr zostanie pominięty i tylko jeden manifest jest obsługiwany na, ten manifest jest modyfikowany.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/out** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**OutputResourceManifests**|Opcjonalny parametr **ciągu** .<br /><br /> Dane wyjściowe manifestu do zasobu typu RT_MANIFEST o określonym identyfikatorze. Zasób ma postać, _\<> pliku [_ **;** _[_ **#** _] < resource_id >]_ , gdzie opcjonalny parametr `resource_id` jest liczbą nieujemną, 16-bitową.<br /><br /> Jeśli żadna `resource_id` nie zostanie określona, zostanie użyta wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/outputresource** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**RegistrarScriptFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku skryptu rejestratora (. RGS), który ma być używany do obsługi manifestu COM bez rejestracji.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/RGS** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**ReplacementsFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa plik, który zawiera wartości dla wymiennych ciągów w pliku skryptu rejestratora (. RGS).<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/replacements** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**ResourceOutputFileName**|Opcjonalny parametr **ciągu** .<br /><br /> Określa plik zasobów wyjściowych służący do osadzenia manifestu w danych wyjściowych projektu.|  
|**Źródeł**|Opcjonalny parametr `ITaskItem[]`.<br /><br /> Określa listę plików źródłowych manifestu rozdzielonych spacjami.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/manifest** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**SuppressDependencyElement**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, generuje manifest bez elementów zależności. Jeśli ten parametr jest `true`, należy również określić parametr zadania **ManifestFromManagedAssemblyMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/nodependency** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**SuppressStartupBanner**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/nologo** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**Katalog trackerlogdirectory**|Opcjonalny parametr `String`.<br /><br /> Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.|  
|**TypeLibraryFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku biblioteki typów (. tlb). W przypadku określenia tego parametru należy także określić parametr zadania **ComponentFileNameMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/TLB** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**UpdateFileHashes**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, oblicza wartość skrótu plików w ścieżce określonej przez parametr zadania **UpdateFileHashesSearchPathMT** , a następnie aktualizuje wartość atrybutu **hash** elementu **pliku** manifestu przy użyciu wartości obliczanej.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/hashupdate** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Zobacz również parametr **UpdateFileHashesSearchPath** w tej tabeli.|  
|**UpdateFileHashesSearchPath**|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę wyszukiwania do użycia podczas aktualizowania skrótów plików. Użyj tego parametru z parametrem zadania **UpdateFileHashesMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz **UpdateFileHashes** parametr w tej tabeli.|  
|**VerboseOutput**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, wyświetla pełne informacje o debugowaniu.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/verbose** w pliku "Mt. exe" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
