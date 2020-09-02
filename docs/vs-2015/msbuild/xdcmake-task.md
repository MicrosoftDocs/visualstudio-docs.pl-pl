---
title: XDCMake — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c16c92b41aa0635ecb24d83e30e2c347620b2c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675537"
---
# <a name="xdcmake-task"></a>XDCMake — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija narzędzie dokumentacji XML (xdcmake.exe), które scala pliki komentarzy dokumentów XML (. xdc) w pliku XML.  
  
 Plik. xdc jest tworzony podczas dostarczania komentarzy do dokumentacji w Visual C++ kodzie źródłowym i kompilowania przy użyciu opcji kompilatora [/doc](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) . Aby uzyskać więcej informacji, zobacz [odwołania xdcmake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [strony właściwości narzędzia generatora dokumentów XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)i opcji pomocy wiersza polecenia (**/?**) dla xdcmake.exe.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie narzędzie xdcmake.exe obsługuje kilka opcji wiersza polecenia. Dodatkowe opcje są obsługiwane w przypadku określenia opcji wiersza polecenia **/Old** .  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry zadania **xdcmake** .  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Opcjonalny parametr **String []** .<br /><br /> Określa co najmniej jeden plik. xdc do scalenia.<br /><br /> Aby uzyskać więcej informacji, zobacz Opis **dodatkowych plików dokumentów** w [stronach właściwości narzędzia Generator dokumentów XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Zobacz również opcje wiersza polecenia **/Old** i **/FS** dla xdcmake.exe.|  
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji określona w wierszu polecenia. Na przykład "*/option1/option2 Option #*". Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez żaden inny parametr zadania **xdcmake** .<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołania xdcmake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [strony właściwości narzędzia generatora dokumentów XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)i pomoc w wierszu polecenia (**/?**) dla xdcmake.exe.|  
|**DocumentLibraryDependencies**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` bieżący projekt ma zależność od projektu biblioteki statycznej (. lib) w rozwiązaniu, pliki. xdc dla tego projektu biblioteki są zawarte w pliku XML wyjściowym dla bieżącego projektu.<br /><br /> Aby uzyskać więcej informacji, zobacz Opis **zależności biblioteki dokumentów** w [stronach właściwości narzędzia Generator dokumentów XML](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**Plik_wyjściowy**|Opcjonalny parametr **ciągu** .<br /><br /> Zastępuje domyślną nazwę pliku wyjściowego. Nazwa domyślna pochodzi od nazwy pierwszego pliku. xdc, który jest przetwarzany.<br /><br /> Aby uzyskać więcej informacji, zobacz polecenie **/out:** `filename` w [xdcmake Reference](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac). Zapoznaj się również z opcjami wiersza polecenia **/Old** i **/fo** dla xdcmake.exe.|  
|**ProjectName**|Opcjonalny parametr **ciągu** .<br /><br /> Nazwa bieżącego projektu.|  
|**SlashOld**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , włącza dodatkowe opcje xdcmake.exe.<br /><br /> Aby uzyskać więcej informacji, zobacz **/Old** opcji wiersza polecenia dla xdcmake.exe.|  
|**Źródła**|Wymagany parametr interfejsu `ITaskItem[]`.<br /><br /> Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** Option in [xdcmake Reference](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog dziennika śledzenia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
