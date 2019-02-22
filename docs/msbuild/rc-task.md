---
title: RC — zadanie | Dokumentacja firmy Microsoft
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
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a69649a7babacb0fe08b483380214f17f2e582f8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603355"
---
# <a name="rc-task"></a>RC — Zadanie
Opakowuje narzędzie kompilatora zasobów systemu Microsoft Windows *rc.exe*. **RC** zadań kompiluje zasoby, takie jak kursorów, ikony, mapy bitowe, okna dialogowe i czcionek, do zasobu (*.res*) pliku. Aby uzyskać więcej informacji, zobacz [kompilator zasobów](https://docs.microsoft.com/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania RC. Większość parametrów zadania oraz kilka zestawów parametrów, odpowiada opcji wiersza polecenia.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Opcjonalnie **String []** parametru.<br /><br /> Dodaje katalog do listy katalogów przeszukiwanych w poszukiwaniu plików dołączanych.<br /><br /> Aby uzyskać więcej informacji, zobacz **/I** opcji [przy użyciu RC (RC wiersza polecenia)](http://go.microsoft.com/fwlink/?LinkId=155730).|
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.<br /><br /> Lista opcji wiersza polecenia; na przykład /\<opcja1 > /\<opcja2 > /\<opcja #>. Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez inne **RC** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [przy użyciu RC (RC wiersza polecenia)](http://go.microsoft.com/fwlink/?LinkId=155730).|
|**Kultury**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa identyfikator ustawień regionalnych, który reprezentuje kulturę używaną w zasobach.<br /><br /> Aby uzyskać więcej informacji, zobacz **/l** opcji [przy użyciu RC (RC wiersza polecenia)](http://go.microsoft.com/fwlink/?LinkId=155730).|
|**IgnoreStandardIncludePath**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia sprawdzanie zmienną środowiskową INCLUDE podczas wyszukiwania plików nagłówkowych lub plików zasobów przez kompilator zasobów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/x** opcji [przy użyciu RC (RC wiersza polecenia)](http://go.microsoft.com/fwlink/?LinkId=155730).|
|**NullTerminateStrings**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, wartość null kończy wszystkie ciągi w tablicy ciągów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji [przy użyciu RC (RC wiersza polecenia)](http://go.microsoft.com/fwlink/?LinkId=155730).|
|**PreprocessorDefinitions**|Opcjonalnie **String []** parametru.<br /><br /> Należy zdefiniować co najmniej jeden symboli preprocesora kompilatora zasobów. Określ listę symbole makra.<br /><br /> Aby uzyskać więcej informacji, zobacz **/d** opcji [przy użyciu RC (RC wiersza polecenia)](http://go.microsoft.com/fwlink/?LinkId=155730). Zobacz też **UndefinePreprocessorDefinitions** w tej tabeli.|
|**ResourceOutputFileName**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę pliku zasobów. Określ nazwę pliku zasobu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/fo** opcji [przy użyciu RC (RC wiersza polecenia)](http://go.microsoft.com/fwlink/?LinkId=155730).|
|**ShowProgress**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, wyświetla komunikaty, które składać sprawozdania z postępów kompilatora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/v** opcji [przy użyciu RC (RC wiersza polecenia)](http://go.microsoft.com/fwlink/?LinkId=155730).|
|**Element źródłowy**|Wymagane `ITaskItem[]` parametru.<br /><br /> Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.|
|**SuppressStartupBanner**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, wpisz **/?** Opcja wiersza polecenia, a następnie zobacz **/nologo** opcji.|
|**TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|
|**UndefinePreprocessorDefinitions**|Usuń definicje symboli preprocesora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/u** opcji [przy użyciu RC (RC wiersza polecenia)](http://go.microsoft.com/fwlink/?LinkId=155730). Zobacz też **PreprocessorDefinitions** w tej tabeli.|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)