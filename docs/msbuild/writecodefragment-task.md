---
title: WriteCodeFragment — Zadanie | Microsoft Docs
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
ms.openlocfilehash: 3745e1c2f300c860d281752a0bf81359806c5d5e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567401"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment — zadanie
Generuje plik kodu tymczasowego z określonego wygenerowanego fragmentu kodu. Nie usuwa pliku.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `WriteCodeFragment`.

|Parametr|Opis|
|---------------|-----------------|
|`AssemblyAttributes`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Opis atrybutów do zapisania. Element `Include` wartość jest pełną nazwą typu atrybutu, na przykład "System. AssemblyVersionAttribute".<br /><br /> Każde metadane to para nazwa-wartość parametru, który musi być typu `String`. Niektóre atrybuty zezwalają tylko na argumenty konstruktora pozycyjnego. Można jednak użyć takich argumentów w dowolnym atrybucie. Aby ustawić atrybuty konstruktora pozycyjnyego, użyj nazw metadanych przypominających "_Parameter1", "_Parameter2" i tak dalej.<br /><br /> Indeks parametru nie może zostać pominięty.|
|`Language`|Wymagany `String` parametr.<br /><br /> Określa język kodu do wygenerowania.<br /><br /> `Language` może być dowolnym językiem, dla którego jest dostępny dostawca CodeDom, na przykład "C#" lub "VisualBasic". Emitowany plik będzie miał domyślne rozszerzenie nazwy pliku dla tego języka.|
|`OutputDirectory`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa folder docelowy dla wygenerowanego kodu, zazwyczaj folder pośredni.|
|`OutputFile`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa ścieżkę pliku, który został wygenerowany. Jeśli ten parametr jest ustawiony przy użyciu nazwy pliku, folder docelowy jest dołączany do nazwy pliku. Jeśli jest ustawiona przy użyciu elementu głównego, folder docelowy jest ignorowany.<br /><br /> Jeśli ten parametr nie jest ustawiony, nazwa pliku wyjściowego jest folderem docelowym, dowolną nazwą pliku i Domyślnym rozszerzeniem nazwy pliku dla określonego języka.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
