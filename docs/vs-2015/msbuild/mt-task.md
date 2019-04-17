---
title: MT — zadanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 93fd3bcff6fa16a4fb28521c58ff2caad6edafbb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667914"
---
# <a name="mt-task"></a>MT — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opakowuje narzędziu manifestu Microsoft mt.exe. Aby uzyskać więcej informacji, zobacz "Mt.exe" w [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **MT** zadania. Większość parametrów zadania oraz kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
> [!NOTE]
>  Dokumentacja mt.exe używa łącznika (**-**) jako prefiks dla opcji wiersza polecenia, ale w tym temacie używa ukośnika (**/**). Dopuszczalne jest albo prefiksu.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Opcjonalnie **String []** parametru.<br /><br /> Określa nazwę co najmniej jeden plik manifestu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/manifest** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.<br /><br /> Listę opcji wiersza polecenia. Na przykład "*/option1 /option2 /option#*". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez inne **MT** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz "Mt.exe" w [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**assemblyIdentity**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa wartości atrybutu **assemblyIdentity** elemencie manifestu. Określ rozdzieloną przecinkami listę, gdzie znajduje się pierwszy składnik wartości `name` atrybutu, a następnie pary nazwa/wartość, które mają następującą formę  *\<nazwa atrybutu > = < attribute_value >*.<br /><br /> Aby uzyskać więcej informacji, zobacz **/identity** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ComponentFileName**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę biblioteki dll, które zamierzasz kompilacji z plików .rgs lub .tlb. Ten parametr jest wymagany, jeśli określisz **RegistrarScriptFile** lub **Plik_biblioteki_typów** MT parametrów zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/dll** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**DependencyInformationFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa plik informacji o zależnościach, używany przez program Visual Studio do śledzenia informacji o zależnościach kompilacji dla narzędzia manifestu.|  
|**EmbedManifest**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, osadza plik manifestu w zestawie. Jeśli `false`, tworzy jako autonomiczny plik manifestu.|  
|**EnableDPIAwareness**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, dodaje do manifestu informacje, które oznacza aplikację jako obsługującą ustawienia DPI. Pisanie aplikacji obsługującą ustawienia DPI sprawia, że interfejs użytkownika wyglądać konsekwentnie w wielu ustawień o wysokiej rozdzielczości DPI.<br /><br /> Aby uzyskać więcej informacji, zobacz "Wysokiej rozdzielczości" w [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**GenerateCatalogFiles**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, generuje pliki definicji (.cdf) w katalogu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/makecdfs** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**GenerateCategoryTags**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, powoduje, że tagi kategorii do wygenerowania. Jeśli ten parametr jest `true`, **ManifestFromManagedAssemblyMT** parametru zadania musi być także określona.<br /><br /> Aby uzyskać więcej informacji, zobacz **/category** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**InputResourceManifests**|Opcjonalnie **ciąg** parametru.<br /><br /> Dane wejściowe manifestu z zasobu typu RT_MANIFEST, który ma określony identyfikator. Określ zasób w postaci  _\<Plik > [_**;** _[_**#**_] < Identyfikator_zasobu_2 >]_, gdzie opcjonalnego `resource_id` parametr jest liczbą nieujemną, 16-bitowych.<br /><br /> Jeśli nie `resource_id` jest określona, używana jest wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz **/inputresource** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ManifestFromManagedAssembly**|Opcjonalnie **ciąg** parametru.<br /><br /> Generuje manifest z określonego zestawu zarządzanego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/managedassemblyname** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ManifestToIgnore**|Opcjonalnie **ciąg** parametru.<br /><br /> (Nie jest używany.)|  
|**OutputManifestFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę manifeście danych wyjściowych. Jeśli ten parametr zostanie pominięty, tylko jeden manifest jest on obsługiwany przez ten manifest zostanie zmodyfikowany w miejscu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/out** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**OutputResourceManifests**|Opcjonalnie **ciąg** parametru.<br /><br /> Dane wyjściowe manifestu do zasobu typu RT_MANIFEST, który ma określony identyfikator. Zasób jest w postaci  _\<Plik > [_**;** _[_**#**_] < Identyfikator_zasobu_2 >]_, gdzie opcjonalnego `resource_id` parametr jest liczbą nieujemną, 16-bitowych.<br /><br /> Jeśli nie `resource_id` jest określona, używana jest wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz **/outputresource** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**RegistrarScriptFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę pliku skryptu (.rgs) rejestratora, do użycia obsługę rejestracji wolnego modelu COM manifestu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/rgs** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ReplacementsFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa plik, który zawiera wartości dla wymienialnych ciągów w pliku skryptu (.rgs) rejestratora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/replacements** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ResourceOutputFileName**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa plik zasobów wynikowych, które są używane do osadzania manifestu w danych wyjściowych projektu.|  
|**Źródła**|Opcjonalnie `ITaskItem[]` parametru.<br /><br /> Określa listę plików źródłowych manifestu, rozdzielone spacjami.<br /><br /> Aby uzyskać więcej informacji, zobacz **/manifest** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**SuppressDependencyElement**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, generuje manifest bez zależności elementów. Jeśli ten parametr jest `true`, również określić **ManifestFromManagedAssemblyMT** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nodependency** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**SuppressStartupBanner**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**TrackerLogDirectory**|Opcjonalnie `String` parametru.<br /><br /> Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.|  
|**TypeLibraryFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę pliku biblioteki (.tlb) typów. W przypadku określenia tego parametru należy także określić **ComponentFileNameMT** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/TLB** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**UpdateFileHashes**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, oblicza wartość skrótu pliku w ścieżce określonej przez **UpdateFileHashesSearchPathMT** parametru zadania, a następnie aktualizuje wartość **skrótu** atrybut **pliku** elemencie manifestu za pomocą wartości obliczanej.<br /><br /> Aby uzyskać więcej informacji, zobacz **/hashupdate** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też **UpdateFileHashesSearchPath** parametru w tej tabeli.|  
|**UpdateFileHashesSearchPath**|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę szukania używaną podczas aktualizacji plików skrótu. Użyj tego parametru z **UpdateFileHashesMT** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **UpdateFileHashes** parametru w tej tabeli.|  
|**VerboseOutput**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, wyświetla pełne informacje debugowania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/ verbose** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
