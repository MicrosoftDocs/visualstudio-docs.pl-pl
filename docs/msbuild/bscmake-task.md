---
title: BscMake — Zadanie | Microsoft Docs
description: Dowiedz się więcej na temat BscMake, w którym zawinięte zostało narzędzie do konserwacji informacji o przeglądaniu bscmake.exe. Środowisko IDE programu Visual Studio nie używa już BscMake.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7618d7e4e16de151c296d66a0c5798475f7ca43
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353281"
---
# <a name="bscmake-task"></a>BscMake, zadanie

> [!IMPORTANT]
> BscMake nie jest już używana przez środowisko IDE programu Visual Studio. Ponieważ program Visual Studio 2008, informacje o przeglądaniu są automatycznie przechowywane w pliku *. sdf* w folderze *rozwiązania* .

 Pakuje narzędzie do konserwacji informacji przeglądarki Microsoft (*bscmake.exe*).  Narzędzie *bscmake.exe* kompiluje plik informacji o przeglądaniu (*BSC*) z plików przeglądarki źródłowej (*. sbr*), które są tworzone podczas kompilacji. Użyj **Przeglądarka obiektów** , aby wyświetlić plik *. bsc* . Aby uzyskać więcej informacji, zobacz [BSCMAKE Reference](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **BSCMAKE** . Większość parametrów zadań odpowiada opcji wiersza polecenia.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji określona w wierszu polecenia. Na przykład/ \<option1>  / \<option2>  / \<option#> . Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez żaden inny parametr zadania **BSCMAKE** .<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Plik_wyjściowy**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku, która zastępuje domyślną nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/o** opcja w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , wymusza nieprzyrostową kompilację. Pełna, nieprzyrostowa kompilacja odbywa się niezależnie od tego, czy plik *. bsc* istnieje i uniemożliwia obcinanie plików *. sbr* .<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Źródeł**|Opcjonalny parametr **ITaskItem []** .<br /><br /> Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.|
|**SuppressStartupBanner**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/nologo** w opcjach [BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog dziennika śledzenia.|

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
