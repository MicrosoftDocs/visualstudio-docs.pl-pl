---
title: Zadanie RC | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 13ae844759cb73de6dc7bcce6c8898c21132f9d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632917"
---
# <a name="rc-task"></a>RC — Zadanie

Zawija narzędzie Kompilator zasobów systemu Microsoft Windows, *rc.exe*. Zadanie **RC** kompiluje zasoby, takie jak kursory, ikony, mapy bitowe, okna dialogowe i czcionki, w plik zasobu (*.res*). Aby uzyskać więcej informacji, zobacz [Kompilator zasobów](/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania rc. Większość parametrów zadania i kilka zestawów parametrów odpowiada opcji wiersza polecenia.

|Parametr|Opis|
|---------------|-----------------|
|**DodatkoweInobserwająKatary**|Parametr **Opcjonalny ciąg[].**<br /><br /> Dodaje katalog do listy katalogów, które są wyszukiwane pliki dołączania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/I** opcja [w Using RC (rc command line)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Dodatkoweopcje**|Opcjonalny parametr **String.**<br /><br /> Lista opcji wiersza polecenia; na przykład\</ option1>\</ option2>\</ option#>. Ten parametr służy do określania opcji wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania **rc.**<br /><br /> Aby uzyskać więcej informacji, zobacz opcje w [temacie Używanie rc (wiersza polecenia RC).](/windows/win32/menurc/using-rc-the-rc-command-line-)|
|**Kultury**|Opcjonalny parametr **String.**<br /><br /> Określa identyfikator ustawień regionalnych reprezentujący kulturę używaną w zasobach.<br /><br /> Aby uzyskać więcej informacji, zobacz **/l** opcja [w using RC (rc command line)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**IgnoreStandardIncludePath**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`program ,uniemożliwia kompilatorowi zasobów sprawdzanie zmiennej środowiskowej INCLUDE podczas wyszukiwania plików nagłówkowych lub plików zasobów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/x** opcja [w Using RC (wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Ciągi NullTerminate**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`, null kończy wszystkie ciągi w tabeli ciągów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcja w [Using RC (rc wiersz polecenia)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Definicje przedtwarze**|Parametr **Opcjonalny ciąg[].**<br /><br /> Zdefiniuj jeden lub więcej symboli preprocesora dla kompilatora zasobów. Określ listę symboli makr.<br /><br /> Aby uzyskać więcej informacji, zobacz **/d** opcja [w Using RC (rc wiersz polecenia)](/windows/win32/menurc/using-rc-the-rc-command-line-). Zobacz także **UndefinePreprocessorDefinitions** w tej tabeli.|
|**Nazwa pliku ResourceOutputFile**|Opcjonalny parametr **String.**<br /><br /> Określa nazwę pliku zasobów. Określ nazwę pliku zasobu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/fo** opcja w [Using RC (rc wiersz polecenia)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**ShowProgress (Proces pokażeń)**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`, wyświetla komunikaty, które raport na temat postępu kompilatora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/v** opcja [w Using RC (rc wiersz polecenia)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Źródła**|Wymagany parametr interfejsu `ITaskItem[]`.<br /><br /> Definiuje tablicę elementów pliku źródłowego MSBuild, które mogą być używane i emitowane przez zadania.|
|**SuppressStartupBanner (SuppressStartupBanner)**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`program Zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji po uruchomieniu zadania.<br /><br /> Aby uzyskać więcej informacji, wpisz **/?** opcji wiersza polecenia, a następnie zobacz opcję **/nologo.**|
|**TrackerLogDirectory (TrackerLogDirectory)**|Opcjonalny parametr **String.**<br /><br /> Określa katalog dziennika modułu śledzącego.|
|**DefinePreprocessorDefinitions**|Niedefiń symbolu preprocesora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/u** opcja [w Using RC (rc wiersz polecenia)](/windows/win32/menurc/using-rc-the-rc-command-line-). Zobacz także **PreprocessorDefinitions** w tej tabeli.|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)