---
title: RC — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 075b3d9201cc17537d62bbe467cc8fa6d3558c35
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773104"
---
# <a name="rc-task"></a>RC — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Opakowuje narzędzie kompilatora zasobów systemu Microsoft Windows rc.exe. **RC** zadań kompiluje zasoby, takie jak kursorów, ikony, mapy bitowe, okna dialogowe i czcionek, w pliku zasobów (.res). Aby uzyskać więcej informacji, zobacz "Kompilator zasobów" w [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry RCtask. Większość parametrów zadania oraz kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Opcjonalnie **String []** parametru.<br /><br /> Dodaje katalog do listy katalogów przeszukiwanych w poszukiwaniu plików dołączanych.<br /><br /> Aby uzyskać więcej informacji, zobacz **/I** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.<br /><br /> Lista przykład wiersza polecenia optionsor **"**_/option1 /option2 /option#_". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez inne **RC** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**Kultury**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa identyfikator ustawień regionalnych, który reprezentuje kulturę używaną w zasobach.<br /><br /> Aby uzyskać więcej informacji, zobacz **/l** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**IgnoreStandardIncludePath**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia sprawdzanie zmienną środowiskową INCLUDE podczas wyszukiwania plików nagłówkowych lub plików zasobów przez kompilator zasobów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/x** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**NullTerminateStrings**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, wartość null kończy wszystkie ciągi w tablicy ciągów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**PreprocessorDefinitions**|Opcjonalnie **String []** parametru.<br /><br /> Należy zdefiniować co najmniej jeden symboli preprocesora kompilatora zasobów. Określ listę symbole makra.<br /><br /> Aby uzyskać więcej informacji, zobacz **/d** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web. Zobacz też **UndefinePreprocessorDefinitions** w tej tabeli.|  
|**ResourceOutputFileName**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę pliku zasobów. Określ nazwę pliku zasobu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/fo** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**ShowProgress**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, wyświetla komunikaty, które składać sprawozdania z postępów kompilatora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/v** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**Element źródłowy**|Wymagane `ITaskItem[]` parametru.<br /><br /> Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, wpisz **/?** Opcja wiersza polecenia, a następnie zobacz **/nologo** opcji.|  
|**TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
|**UndefinePreprocessorDefinitions**|Usuń definicje symboli preprocesora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/u** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web. Zobacz też **PreprocessorDefinitions** w tej tabeli.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
