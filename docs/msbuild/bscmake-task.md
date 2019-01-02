---
title: Bscmake — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f5a8d7f60793bbd6864fdfa98fc1864d1612955
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887451"
---
# <a name="bscmake-task"></a>Bscmake — zadanie
> [!IMPORTANT]
>  BscMake nie jest już używany przez program Visual Studio IDE. Od programu Visual Studio 2008, informacji o przeglądaniu znajduje się automatycznie w *.sdf* w pliku *rozwiązania* folderu.  
  
 Opakowuje Microsoft Przeglądaj informacje narzędzie konserwacji (*bscmake.exe*).  *Bscmake.exe* narzędzia do kompilacji pliku informacyjnego przeglądarki (*.bsc*) z pliki przeglądarki źródeł (*.sbr*) które są tworzone podczas kompilacji. Użyj **przeglądarki obiektów** do wyświetlania *.bsc* pliku. Aby uzyskać więcej informacji, zobacz [odwołanie BSCMAKE](/cpp/build/reference/bscmake-reference).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **BscMake** zadania. Większość parametrów zadania odpowiada opcji wiersza polecenia.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.<br /><br /> Lista opcji określonych w wierszu polecenia. Na przykład /\<opcja1 > /\<opcja2 > /\<opcja #>. Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez inne **BscMake** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [opcje BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**OutputFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę pliku, która zastępuje domyślną nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/o** opcji [opcje BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**PreserveSBR**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, wymusza nieprzyrostowa kompilacji. Pełne, nieprzyrostowa kompilacji odbywa się niezależnie od tego, czy *.bsc* plik istnieje i zapobiega *.sbr* pliki obcięcia.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji [opcje BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**Źródła**|Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji [opcje BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**Katalog TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)