---
title: Bscmake — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ed246255fc20b9660d24f234767fdeb451102f8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684543"
---
# <a name="bscmake-task"></a>BscMake — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[WAŻNE]
> bscmake nie jest już używany przez program Visual Studio IDE. Od programu Visual Studio 2008 informacji o przeglądaniu jest automatycznie przechowywany w pliku .sdf w folderze rozwiązania.  
  
 Opakowuje Microsoft Przeglądaj informacje narzędzie konserwacji (bscmake.exe).  Narzędzie bscmake.exe kompilacji pliku informacyjnego przeglądarki (.bsc) z pliki przeglądarki źródeł (.sbr), które są tworzone podczas kompilacji. Użyj **przeglądarki obiektów** do wyświetlenia pliku .bsc. Aby uzyskać więcej informacji, zobacz [odwołanie BSCMAKE](https://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **BscMake** zadania. Większość parametrów zadania odpowiada opcji wiersza polecenia.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.<br /><br /> Lista opcji określonych w wierszu polecenia. Na przykład "/*opcja1* /*opcja2* /*opcja #*". Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez inne **BscMake** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [opcje BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**OutputFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę pliku, która zastępuje domyślną nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/o** opcji [opcje BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**PreserveSBR**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, wymusza nieprzyrostowa kompilacji. Pełne, nieprzyrostowa kompilacji odbywa się niezależnie od tego, czy istnieje plik .bsc i zapobiega obcinania plików SBR.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji [opcje BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**Źródła**|Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji [opcje BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
