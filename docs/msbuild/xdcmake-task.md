---
title: Xdcmake — zadanie | Dokumentacja firmy Microsoft
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
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a830639d8e69a331c2d81c6012d0ea7e6fcfb848
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990197"
---
# <a name="xdcmake-task"></a>XDCMake — Zadanie
Opakowuje narzędzie dokumentacji XML (*xdcmake.exe*), który scala komentarza dokumentu XML (*.xdc*) pliki do *.xml* pliku.  
  
 *.Xdc* tworzony jest plik po podaniu komentarzy do dokumentacji w kodzie źródłowym języka Visual C++ i kompilacji za pomocą [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [xdcmake — dokumentacja](/cpp/ide/xdcmake-reference), [strony właściwości narzędzie generowania dokumentów XML](/cpp/ide/xml-document-generator-tool-property-pages)i opcji Pomoc w wierszu polecenia (**/?**) dla *xdcmake.exe* .  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie *xdcmake.exe* narzędzie obsługuje kilka opcji wiersza polecenia. Dodatkowe opcje są obsługiwane w przypadku określenia **/stare** opcji wiersza polecenia.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **XDCMake** zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Opcjonalnie **String []** parametru.<br /><br /> Określa jedną lub więcej dodatkowych *.xdc* pliki do scalania.<br /><br /> Aby uzyskać więcej informacji, zobacz **dodatkowe pliki dokumentów** opis [strony właściwości narzędzie generowania dokumentów XML](/cpp/ide/xml-document-generator-tool-property-pages). Zobacz też **/stare** i **/Fs** opcje wiersza polecenia dla *xdcmake.exe*.|  
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.<br /><br /> Lista opcji określonych w wierszu polecenia. Na przykład /\<opcja1 > /\<opcja2 > /\<opcja #>. Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez inne **XDCMake** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz [xdcmake — dokumentacja](/cpp/ide/xdcmake-reference), [strony właściwości narzędzie generowania dokumentów XML](/cpp/ide/xml-document-generator-tool-property-pages)i pomoc w wierszu polecenia (**/?**) dla *xdcmake.exe*.|  
|**DocumentLibraryDependencies**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true` i bieżący projekt zależny od biblioteki statycznej (*.lib*) projektu w rozwiązaniu, *.xdc* pliki w projekcie biblioteki są zawarte w *.xml* pliku danych wyjściowych dla bieżącego projektu.<br /><br /> Aby uzyskać więcej informacji, zobacz **zależności biblioteki dokumentów** opis [strony właściwości narzędzie generowania dokumentów XML](/cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Przesłania domyślną nazwę pliku wyjściowego. Domyślną nazwą jest tworzony na podstawie nazwy pierwszego *.xdc* pliku, który jest przetwarzany.<br /><br /> Aby uzyskać więcej informacji, zobacz **/out:\<nazwa pliku >** opcji [xdcmake — dokumentacja](/cpp/ide/xdcmake-reference). Zobacz też **/stare** i **/Fo** opcje wiersza polecenia dla *xdcmake.exe*.|  
|**ProjectName**|Opcjonalnie **ciąg** parametru.<br /><br /> Nazwa bieżącego projektu.|  
|**SlashOld**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, umożliwia dodatkowe *xdcmake.exe* opcje.<br /><br /> Aby uzyskać więcej informacji, zobacz **/stare** opcji wiersza polecenia dla *xdcmake.exe*.|  
|**Źródła**|Wymagane `ITaskItem[]` parametru.<br /><br /> Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji [xdcmake — dokumentacja](/cpp/ide/xdcmake-reference).|  
|**Katalog TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)