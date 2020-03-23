---
title: Zadanie WriteCodeFragment | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ab604b23a99ab2dd62adca6076168fe264ab1b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630695"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment — zadanie

Generuje tymczasowy plik kodu z określonego wygenerowanego fragmentu kodu. Nie usuwa pliku.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `WriteCodeFragment` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AssemblyAttributes`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Opis atrybutów do napisania. Wartość `Include` elementu jest pełną nazwą typu atrybutu, na przykład "System.AssemblyVersionAttribute".<br /><br /> Każde metadane to para nazwa-wartość parametru, `String`która musi być typu . Niektóre atrybuty zezwalają tylko na argumenty konstruktora pozycyjnego. Można jednak użyć takich argumentów w dowolnym atrybucie. Aby ustawić atrybuty konstruktora pozycyjnego, należy użyć nazw metadanych, które przypominają "_Parameter1", "_Parameter2" i tak dalej.<br /><br /> Nie można pominąć indeksu parametrów.|
|`Language`|Wymagany parametr interfejsu `String`.<br /><br /> Określa język kodu do wygenerowania.<br /><br /> `Language`może to być dowolny język, dla którego dostawca CodeDom jest dostępny, na przykład "C#" lub "VisualBasic". Emitowany plik będzie miał domyślne rozszerzenie nazwy pliku dla tego języka.|
|`OutputDirectory`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa folder docelowy wygenerowanego kodu, zazwyczaj folder pośredni.|
|`OutputFile`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Określa ścieżkę wygenerowanego pliku. Jeśli ten parametr jest ustawiany przy użyciu nazwy pliku, folder docelowy jest dołączany do nazwy pliku. Jeśli jest ustawiona przy użyciu katalogu głównego, folder docelowy jest ignorowany.<br /><br /> Jeśli ten parametr nie jest ustawiony, nazwa pliku wyjściowego jest folderem docelowym, dowolną nazwą pliku i domyślnym rozszerzeniem nazwy pliku dla określonego języka.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
