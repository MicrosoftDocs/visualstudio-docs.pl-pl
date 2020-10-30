---
title: RC — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania RC do zawijania narzędzia kompilatora zasobów systemu Microsoft Windows, rc.exe, które kompiluje zasoby w pliku. res.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
- RC task (MSBuild (C++))
- MSBuild (C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94a1babf518a3579246903f6479f999d8912dfe5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048788"
---
# <a name="rc-task"></a>RC — Zadanie

Zawija narzędzie kompilatora zasobów systemu Microsoft Windows, *rc.exe* . Zadanie **RC** kompiluje zasoby, takie jak kursory, ikony, mapy bitowe, okna dialogowe i czcionki, do pliku zasobów ( *. res* ). Aby uzyskać więcej informacji, zobacz [kompilator zasobów](/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania RC. Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Opcjonalny parametr **String []** .<br /><br /> Dodaje katalog do listy katalogów, które są przeszukiwane w poszukiwaniu plików dołączanych.<br /><br /> Aby uzyskać więcej informacji, zobacz **/i** Option in [using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji wiersza polecenia; na przykład/ \<option1>  / \<option2>  / \<option#> . Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania **RC** .<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w temacie [using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Kultura**|Opcjonalny parametr **ciągu** .<br /><br /> Określa identyfikator ustawień regionalnych, który reprezentuje kulturę używaną w zasobach.<br /><br /> Aby uzyskać więcej informacji, zobacz **/l** opcji w artykule [using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**IgnoreStandardIncludePath**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` zapobiega sprawdzaniu przez kompilator zasobów zmiennej środowiskowej INCLUDE podczas wyszukiwania plików nagłówkowych lub plików zasobów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/x** Option in [using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**NullTerminateStrings**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , null-kończy wszystkie ciągi w tabeli ciągów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji w artykule [using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**PreprocessorDefinitions**|Opcjonalny parametr **String []** .<br /><br /> Zdefiniuj jeden lub więcej symboli preprocesora dla kompilatora zasobów. Określ listę symboli makr.<br /><br /> Aby uzyskać więcej informacji, zobacz **/d** Option in [using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Zobacz też **UndefinePreprocessorDefinitions** w tej tabeli.|
|**ResourceOutputFileName**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku zasobów. Określ nazwę pliku zasobu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/fo** Option in [using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**ShowProgress**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , wyświetla komunikaty, które są raportowane na postęp kompilatora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/v** opcja w artykule [using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Element źródłowy**|Wymagany parametr interfejsu `ITaskItem[]`.<br /><br /> Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.|
|**SuppressStartupBanner**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, wpisz **/?** Opcja wiersza polecenia, a następnie zobacz opcję **/nologo** .|
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog dziennika śledzenia.|
|**UndefinePreprocessorDefinitions**|Usuń definicję symbolu preprocesora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/u** opcji w artykule [using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Zobacz też **PreprocessorDefinitions** w tej tabeli.|

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)