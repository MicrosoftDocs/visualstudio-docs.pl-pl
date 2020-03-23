---
title: XDCZadumy | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 3c41bfc2015f29cbb73b33df3594b3a3430af3f3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630655"
---
# <a name="xdcmake-task"></a>XDCMake — Zadanie

Zawija narzędzie Dokumentacja XML *(xdcmake.exe),* które scala pliki dokumentu XML *(xdc)* w plik *xml.*

 Plik *.xdc* jest tworzony po podaniu komentarzy dokumentacji w kodzie źródłowym języka C++ i kompilacji przy użyciu opcji kompilatora [/doc.](/cpp/build/reference/doc-process-documentation-comments-c-cpp) Aby uzyskać więcej informacji, zobacz [XDCMake reference](/cpp/build/reference/xdcmake-reference), [Strony właściwości narzędzia generator dokumentów XML](/cpp/build/reference/xml-document-generator-tool-property-pages)i opcja pomocy wiersza polecenia (**/?**) dla *pliku xdcmake.exe*.

## <a name="remarks"></a>Uwagi

 Domyślnie narzędzie *xdcmake.exe* obsługuje kilka opcji wiersza polecenia. Dodatkowe opcje są obsługiwane po określeniu **/old** opcji wiersza polecenia.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **XDCMake.**

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalDocumentFile**|Parametr **Opcjonalny ciąg[].**<br /><br /> Określa jeden lub więcej dodatkowych plików *xdc* do scalenia.<br /><br /> Aby uzyskać więcej informacji, zobacz opis **dodatkowych plików dokumentów** na stronach właściwości Narzędzia [generatora dokumentów XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Zobacz też opcje wiersza polecenia **/old** i **/Fs** dla *pliku xdcmake.exe*.|
|**Dodatkoweopcje**|Opcjonalny parametr **String.**<br /><br /> Lista opcji określonych w wierszu polecenia. Na przykład\</ option1>\</ option2\<> / option#>. Ten parametr służy do określania opcji, które nie są reprezentowane przez żaden inny parametr zadania **XDCMake.**<br /><br /> Aby uzyskać więcej informacji, zobacz [XDCMake reference](/cpp/build/reference/xdcmake-reference), [strony właściwości narzędzia XML Generator dokumentów](/cpp/build/reference/xml-document-generator-tool-property-pages)i pomoc wiersza polecenia (**/?**) dla *pliku xdcmake.exe*.|
|**DocumentLibraryZależności**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true` bieżący projekt ma zależność od projektu biblioteki statycznej (*lib*) w rozwiązaniu, pliki *.xdc* dla tego projektu biblioteki są zawarte w danych wyjściowych pliku *xml* dla bieżącego projektu.<br /><br /> Aby uzyskać więcej informacji, zobacz opis **zależności biblioteki dokumentów** na [stronach właściwości Narzędzia generatora dokumentów XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**Outputfile**|Opcjonalny parametr **String.**<br /><br /> Zastępuje domyślną nazwę pliku wyjściowego. Nazwa domyślna pochodzi od nazwy pierwszego pliku *xdc,* który jest przetwarzany.<br /><br /> Aby uzyskać więcej informacji, zobacz **/out:\<opcja>nazwa pliku** w [XDCMake reference](/cpp/build/reference/xdcmake-reference). Zobacz też opcje wiersza polecenia **/old** i **/Fo** dla *pliku xdcmake.exe*.|
|**Nazwaprojektu**|Opcjonalny parametr **String.**<br /><br /> Nazwa bieżącego projektu.|
|**SlashOld (Cięcie)**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`program , włącza dodatkowe opcje *xdcmake.exe.*<br /><br /> Aby uzyskać więcej informacji, zobacz **/old** command-line option for *xdcmake.exe*.|
|**Źródeł**|Wymagany parametr interfejsu `ITaskItem[]`.<br /><br /> Definiuje tablicę elementów pliku źródłowego MSBuild, które mogą być używane i emitowane przez zadania.|
|**SuppressStartupBanner (SuppressStartupBanner)**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`program Zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji po uruchomieniu zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcja w [XDCMake odwołania](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory (TrackerLogDirectory)**|Opcjonalny parametr **String.**<br /><br /> Określa katalog dziennika modułu śledzącego.|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)