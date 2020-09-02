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
ms.openlocfilehash: d705bff368e813bdd2c7fe2b60ba9ada8f679bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845967"
---
# <a name="mt-task"></a>MT — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija narzędzie manifestu firmy Microsoft, mt.exe. Aby uzyskać więcej informacji, zobacz "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **MT** zadania. Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.  
  
> [!NOTE]
> W dokumentacji mt.exe jest stosowany łącznik ( **-** ) jako prefiks opcji wiersza polecenia, ale w tym temacie jest stosowany ukośnik ( **/** ). Dowolny prefiks jest akceptowalny.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Opcjonalny parametr **String []** .<br /><br /> Określa nazwę jednego lub więcej plików manifestu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/manifest** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji wiersza polecenia. Na przykład "*/option1/option2 Option #*". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr **MT** .<br /><br /> Aby uzyskać więcej informacji, zobacz "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**AssemblyIdentity**|Opcjonalny parametr **ciągu** .<br /><br /> Określa wartości atrybutów elementu **assemblyIdentity** manifestu. Określ listę rozdzielaną przecinkami, gdzie pierwszy składnik jest wartością `name` atrybutu, po którym następuje co najmniej jedna para nazwa/wartość mająca postać, * \<attribute name> =<ATTRIBUTE_VALUE>*.<br /><br /> Aby uzyskać więcej informacji, zobacz **/Identity** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**ComponentFileName**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę biblioteki dołączanej dynamicznie, która ma zostać utworzona na podstawie plików. RGS lub. tlb. Ten parametr jest wymagany, jeśli określono parametry zadania **RegistrarScriptFile** lub **TypeLibraryFile** Mt.<br /><br /> Aby uzyskać więcej informacji, zobacz **/dll** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**DependencyInformationFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa plik informacji o zależnościach używany przez program Visual Studio do śledzenia informacji o zależnościach kompilacji dla narzędzia manifestu.|  
|**EmbedManifest**|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , osadza plik manifestu w zestawie. Jeśli `false` , tworzy jako autonomiczny plik manifestu.|  
|**EnableDPIAwareness**|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , dodaje do informacji manifestu, który oznacza aplikację jako obsługującą dpi. Pisanie aplikacji z obsługą rozdzielczości DPI sprawia, że interfejs użytkownika wygląda spójnie w wielu różnych ustawieniach wyświetlania o wysokiej rozdzielczości DPI.<br /><br /> Aby uzyskać więcej informacji, zobacz "High DPI" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**GenerateCatalogFiles**|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , generuje pliki definicji katalogu (. CDF).<br /><br /> Aby uzyskać więcej informacji, zobacz **/makecdfs** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**GenerateCategoryTags**|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , powoduje, że Tagi kategorii mają być generowane. Jeśli ten parametr ma wartość `true` , należy również określić parametr zadania **ManifestFromManagedAssemblyMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz **/Category** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**InputResourceManifests**|Opcjonalny parametr **ciągu** .<br /><br /> Wprowadź manifest z zasobu typu RT_MANIFEST o określonym identyfikatorze. Określ zasób formularza _ \<file> [_**;** _[_ **#** _] <resource_id>]_, gdzie opcjonalny `resource_id` parametr ma wartość nieujemną, 16-bitową.<br /><br /> Jeśli nie `resource_id` jest określony, zostanie użyta wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz **/inputresource** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**ManifestFromManagedAssembly**|Opcjonalny parametr **ciągu** .<br /><br /> Generuje manifest z określonego zarządzanego zestawu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/managedassemblyname** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**ManifestToIgnore**|Opcjonalny parametr **ciągu** .<br /><br /> (Nieużywane).|  
|**OutputManifestFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę manifestu danych wyjściowych. Jeśli ten parametr zostanie pominięty i tylko jeden manifest jest obsługiwany na, ten manifest jest modyfikowany.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/out** w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**OutputResourceManifests**|Opcjonalny parametr **ciągu** .<br /><br /> Dane wyjściowe manifestu do zasobu typu RT_MANIFEST o określonym identyfikatorze. Zasób ma postać _ \<file> [_**;** _[_ **#** _] <resource_id>]_, gdzie opcjonalny `resource_id` parametr ma wartość nieujemną, 16-bitową.<br /><br /> Jeśli nie `resource_id` jest określony, zostanie użyta wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz **/outputresource** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**RegistrarScriptFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku skryptu rejestratora (. RGS), który ma być używany do obsługi manifestu COM bez rejestracji.<br /><br /> Aby uzyskać więcej informacji, zobacz **/RGS** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**ReplacementsFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa plik, który zawiera wartości dla wymiennych ciągów w pliku skryptu rejestratora (. RGS).<br /><br /> Aby uzyskać więcej informacji, zobacz **/replacements** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**ResourceOutputFileName**|Opcjonalny parametr **ciągu** .<br /><br /> Określa plik zasobów wyjściowych służący do osadzenia manifestu w danych wyjściowych projektu.|  
|**Źródła**|Opcjonalny `ITaskItem[]` parametr.<br /><br /> Określa listę plików źródłowych manifestu rozdzielonych spacjami.<br /><br /> Aby uzyskać więcej informacji, zobacz **/manifest** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**SuppressDependencyElement**|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , generuje manifest bez elementów zależności. Jeśli ten parametr ma wartość `true` , należy również określić parametr zadania **ManifestFromManagedAssemblyMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz **/nodependency** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**SuppressStartupBanner**|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**Katalog trackerlogdirectory**|Opcjonalny `String` parametr.<br /><br /> Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.|  
|**TypeLibraryFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku biblioteki typów (. tlb). W przypadku określenia tego parametru należy także określić parametr zadania **ComponentFileNameMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz **/TLB** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
|**UpdateFileHashes**|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , oblicza wartość skrótu plików w ścieżce określonej przez parametr zadania **UpdateFileHashesSearchPathMT** , a następnie aktualizuje wartość atrybutu **hash** elementu **pliku** manifestu przy użyciu wartości obliczanej.<br /><br /> Aby uzyskać więcej informacji, zobacz **/hashupdate** opcję w "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web. Zobacz również parametr **UpdateFileHashesSearchPath** w tej tabeli.|  
|**UpdateFileHashesSearchPath**|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę wyszukiwania do użycia podczas aktualizowania skrótów plików. Użyj tego parametru z parametrem zadania **UpdateFileHashesMT** .<br /><br /> Aby uzyskać więcej informacji, zobacz **UpdateFileHashes** parametr w tej tabeli.|  
|**VerboseOutput**|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , wyświetla pełne informacje o debugowaniu.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/verbose** w artykule "Mt.exe" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
