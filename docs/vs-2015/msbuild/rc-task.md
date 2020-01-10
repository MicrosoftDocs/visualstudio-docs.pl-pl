---
title: RC — zadanie | Microsoft Docs
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
ms.openlocfilehash: 81f64ec9774410ea55897445836c8633fe98e7bb
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851741"
---
# <a name="rc-task"></a>RC — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija narzędzie kompilatora zasobów systemu Microsoft Windows, RC. exe. Zadanie **RC** kompiluje zasoby, takie jak kursory, ikony, mapy bitowe, okna dialogowe i czcionki, do pliku zasobów (. res). Aby uzyskać więcej informacji, zobacz "kompilator zasobów" w witrynie [MSDN](https://msdn.microsoft.com/) w sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry RCtask. Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Opcjonalny parametr **String []** .<br /><br /> Dodaje katalog do listy katalogów, które są przeszukiwane w poszukiwaniu plików dołączanych.<br /><br /> Aby uzyskać więcej informacji, zobacz **/i** opcji w artykule [using RC (wiersz polecenia RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) w witrynie MSDN w sieci Web.|  
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista przykładowych opcji wiersza polecenia **"** _/option1/option2 Option #_ ". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania **RC** .<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w temacie [using RC (wiersz polecenia RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) w witrynie MSDN w sieci Web.|  
|**Dziedzinie**|Opcjonalny parametr **ciągu** .<br /><br /> Określa identyfikator ustawień regionalnych, który reprezentuje kulturę używaną w zasobach.<br /><br /> Aby uzyskać więcej informacji, zobacz **/l** opcji w artykule [using RC (wiersz polecenia RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) w witrynie MSDN w sieci Web.|  
|**IgnoreStandardIncludePath**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, program zapobiega sprawdzaniu przez kompilator zasobów zmiennej środowiskowej INCLUDE podczas wyszukiwania plików nagłówkowych lub plików zasobów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/x** Option in [using RC (wiersz polecenia RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) w witrynie MSDN w sieci Web.|  
|**NullTerminateStrings**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, null-kończy wszystkie ciągi w tabeli ciągów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji w artykule [using RC (wiersz polecenia RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) w witrynie MSDN w sieci Web.|  
|**PreprocessorDefinitions**|Opcjonalny parametr **String []** .<br /><br /> Zdefiniuj jeden lub więcej symboli preprocesora dla kompilatora zasobów. Określ listę symboli makr.<br /><br /> Aby uzyskać więcej informacji, zobacz **/d** Option in [using RC (wiersz polecenia RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) w witrynie MSDN w sieci Web. Zobacz też **UndefinePreprocessorDefinitions** w tej tabeli.|  
|**ResourceOutputFileName**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku zasobów. Określ nazwę pliku zasobu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/fo** Option in [using RC (wiersz polecenia RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) w witrynie MSDN w sieci Web.|  
|**ShowProgress**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, wyświetla komunikaty, które są raportowane na postęp kompilatora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/v** opcja w artykule [using RC (wiersz polecenia RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) w witrynie MSDN w sieci Web.|  
|**Element źródłowy**|Wymagany `ITaskItem[]` parametr.<br /><br /> Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, wpisz **/?** Opcja wiersza polecenia, a następnie zobacz opcję **/nologo** .|  
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog dziennika śledzenia.|  
|**UndefinePreprocessorDefinitions**|Usuń definicję symbolu preprocesora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/u** opcji w artykule [using RC (wiersz polecenia RC)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) w witrynie MSDN w sieci Web. Zobacz też **PreprocessorDefinitions** w tej tabeli.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
