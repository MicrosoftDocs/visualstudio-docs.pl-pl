---
title: BscMake — Zadanie | Microsoft Docs
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
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acf9c0df17ec0e1bb97c1426d5d312f616de0a8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747373"
---
# <a name="bscmake-task"></a>BscMake, zadanie
> [!IMPORTANT]
> BscMake nie jest już używana przez środowisko IDE programu Visual Studio. Ponieważ program Visual Studio 2008, informacje o przeglądaniu są automatycznie przechowywane w pliku *. sdf* w folderze *rozwiązania* .

 Pakuje narzędzie do konserwacji informacji przeglądarki Microsoft (*BSCMAKE. exe*).  Narzędzie *BSCMAKE. exe* kompiluje plik z informacjami o przeglądaniu (*BSC*) z plików przeglądarki źródłowej ( *. sbr*), które są tworzone podczas kompilacji. Użyj **Przeglądarka obiektów** , aby wyświetlić plik *. bsc* . Aby uzyskać więcej informacji, zobacz [BSCMAKE Reference](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania **BSCMAKE** . Większość parametrów zadań odpowiada opcji wiersza polecenia.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji określona w wierszu polecenia. Na przykład/\<option1 >/\<option2 >/\<option # >. Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez żaden inny parametr zadania **BSCMAKE** .<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Plik_wyjściowy**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku, która zastępuje domyślną nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/o** opcja w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, wymusza nieprzyrostową kompilację. Pełna, nieprzyrostowa kompilacja odbywa się niezależnie od tego, czy plik *. bsc* istnieje i uniemożliwia obcinanie plików *. sbr* .<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Źródeł**|Opcjonalny parametr **ITaskItem []** .<br /><br /> Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.|
|**SuppressStartupBanner**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/nologo** w opcjach [BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog dziennika śledzenia.|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)