---
title: Zadanie BscMake | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 668d42cdb0bc5cfb8dd344aab51ad0c66a838cd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634516"
---
# <a name="bscmake-task"></a>Zadanie BscMake

> [!IMPORTANT]
> BscMake nie jest już używany przez ide programu Visual Studio. Od programu Visual Studio 2008 przeglądanie informacji jest automatycznie przechowywane w pliku *sdf* w folderze *Rozwiązanie.*

 Zawija narzędzie Narzędzia konserwacji informacji przeglądania przez firmę Microsoft *(bscmake.exe).*  Narzędzie *bscmake.exe* tworzy plik informacji przeglądania (*.bsc*) ze źródłowych plików przeglądarki (*.sbr*), które są tworzone podczas kompilacji. Użyj **przeglądarki obiektów,** aby wyświetlić plik *bsc.* Aby uzyskać więcej informacji, zobacz [odwołanie BSCMAKE](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **BscMake.** Większość parametrów zadania odpowiada opcji wiersza polecenia.

|Parametr|Opis|
|---------------|-----------------|
|**Dodatkoweopcje**|Opcjonalny parametr **String.**<br /><br /> Lista opcji określonych w wierszu polecenia. Na przykład\</ option1>\</ option2\<> / option#>. Ten parametr służy do określania opcji, które nie są reprezentowane przez żaden inny parametr zadania **BscMake.**<br /><br /> Aby uzyskać więcej informacji, zobacz opcje w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Outputfile**|Opcjonalny parametr **String.**<br /><br /> Określa nazwę pliku, która zastępuje domyślną nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/o** opcja w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**PrzetworyBR**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`, wymusza kompilację nieekrecyjną. Pełna kompilacja niewkrągła występuje niezależnie od tego, czy istnieje plik *.bsc* i zapobiega obcięciu plików *.sbr.*<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcja w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Źródeł**|Opcjonalny parametr **ITaskItem[].**<br /><br /> Definiuje tablicę elementów pliku źródłowego MSBuild, które mogą być używane i emitowane przez zadania.|
|**SuppressStartupBanner (SuppressStartupBanner)**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`program Zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji po uruchomieniu zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/NOLOGO** opcja w [opcjach BSCMAKE](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory (TrackerLogDirectory)**|Opcjonalny parametr **String.**<br /><br /> Określa katalog dziennika modułu śledzącego.|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
