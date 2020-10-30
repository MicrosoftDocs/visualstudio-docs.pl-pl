---
title: XDCMake — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania XDCMake, aby otoczyć xdcmake.exe narzędzia dokumentacji XML, które scala pliki komentarzy dokumentów XML w pliku XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (C++))
- MSBuild (C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62d1717acee9b8935f176bc10191f044b28a660d
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047271"
---
# <a name="xdcmake-task"></a>XDCMake — Zadanie

Zawija narzędzie dokumentacji XML ( *xdcmake.exe* ), które scala pliki komentarzy dokumentów XML ( *. xdc* ) w pliku *XML* .

 Plik *. xdc* jest tworzony podczas dostarczania komentarzy do dokumentacji w kodzie źródłowym języka C++ i kompilowania przy użyciu opcji kompilatora [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) . Aby uzyskać więcej informacji, zobacz [odwołania xdcmake](/cpp/build/reference/xdcmake-reference), [strony właściwości narzędzia generatora dokumentów XML](/cpp/build/reference/xml-document-generator-tool-property-pages)i opcji pomocy wiersza polecenia ( **/?** ) dla *xdcmake.exe* .

## <a name="remarks"></a>Uwagi

 Domyślnie narzędzie *xdcmake.exe* obsługuje kilka opcji wiersza polecenia. Dodatkowe opcje są obsługiwane w przypadku określenia opcji wiersza polecenia **/Old** .

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **xdcmake** .

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalDocumentFile**|Opcjonalny parametr **String []** .<br /><br /> Określa co najmniej jeden plik *. xdc* do scalenia.<br /><br /> Aby uzyskać więcej informacji, zobacz Opis **dodatkowych plików dokumentów** w [stronach właściwości narzędzia Generator dokumentów XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Zobacz również opcje wiersza polecenia **/Old** i **/FS** dla *xdcmake.exe* .|
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji określona w wierszu polecenia. Na przykład/ \<option1>  / \<option2>  / \<option#> . Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez żaden inny parametr zadania **xdcmake** .<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołania xdcmake](/cpp/build/reference/xdcmake-reference), [strony właściwości narzędzia generatora dokumentów XML](/cpp/build/reference/xml-document-generator-tool-property-pages)i pomoc w wierszu polecenia ( **/?** ) dla *xdcmake.exe* .|
|**DocumentLibraryDependencies**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` bieżący projekt ma zależność od projektu biblioteki statycznej ( *. lib* ) w rozwiązaniu, pliki *. xdc* dla tego projektu biblioteki są zawarte w pliku *XML* wyjściowym dla bieżącego projektu.<br /><br /> Aby uzyskać więcej informacji, zobacz Opis **zależności biblioteki dokumentów** w [stronach właściwości narzędzia Generator dokumentów XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**Plik_wyjściowy**|Opcjonalny parametr **ciągu** .<br /><br /> Zastępuje domyślną nazwę pliku wyjściowego. Nazwa domyślna pochodzi od nazwy pierwszego pliku *. xdc* , który jest przetwarzany.<br /><br /> Aby uzyskać więcej informacji, zobacz polecenie **/out \<filename> :** w [xdcmake Reference](/cpp/build/reference/xdcmake-reference). Zapoznaj się również z opcjami wiersza polecenia **/Old** i **/fo** dla *xdcmake.exe* .|
|**ProjectName**|Opcjonalny parametr **ciągu** .<br /><br /> Nazwa bieżącego projektu.|
|**SlashOld**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , włącza dodatkowe opcje *xdcmake.exe* .<br /><br /> Aby uzyskać więcej informacji, zobacz **/Old** opcji wiersza polecenia dla *xdcmake.exe* .|
|**Źródeł**|Wymagany parametr interfejsu `ITaskItem[]`.<br /><br /> Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.|
|**SuppressStartupBanner**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** Option in [xdcmake Reference](/cpp/build/reference/xdcmake-reference).|
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog dziennika śledzenia.|

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)