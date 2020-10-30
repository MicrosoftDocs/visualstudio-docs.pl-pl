---
title: WriteCodeFragment — Zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania WriteCodeFragment do wygenerowania pliku kodu tymczasowego z określonego wygenerowanego fragmentu kodu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fc96f804541f780da38776d19b19393eb249a4ec
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047466"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment — zadanie

Generuje plik kodu tymczasowego z określonego wygenerowanego fragmentu kodu. Nie usuwa pliku.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `WriteCodeFragment` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AssemblyAttributes`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Opis atrybutów do zapisania. Wartość elementu `Include` to pełna nazwa typu atrybutu, na przykład "System. AssemblyVersionAttribute".<br /><br /> Każde metadane to para nazwa-wartość parametru, który musi być typu `String` . Niektóre atrybuty zezwalają tylko na argumenty konstruktora pozycyjnego. Można jednak użyć takich argumentów w dowolnym atrybucie. Aby ustawić atrybuty konstruktora pozycyjnyego, użyj nazw metadanych przypominających "_Parameter1", "_Parameter2" i tak dalej.<br /><br /> Indeks parametru nie może zostać pominięty.|
|`Language`|Wymagany parametr interfejsu `String`.<br /><br /> Określa język kodu do wygenerowania.<br /><br /> `Language` może to być dowolny język, dla którego jest dostępny dostawca CodeDom, na przykład "C#" lub "VisualBasic". Emitowany plik będzie miał domyślne rozszerzenie nazwy pliku dla tego języka.|
|`OutputDirectory`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa folder docelowy dla wygenerowanego kodu, zazwyczaj folder pośredni.|
|`OutputFile`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa ścieżkę pliku, który został wygenerowany. Jeśli ten parametr jest ustawiony przy użyciu nazwy pliku, folder docelowy jest dołączany do nazwy pliku. Jeśli jest ustawiona przy użyciu elementu głównego, folder docelowy jest ignorowany.<br /><br /> Jeśli ten parametr nie jest ustawiony, nazwa pliku wyjściowego jest folderem docelowym, dowolną nazwą pliku i Domyślnym rozszerzeniem nazwy pliku dla określonego języka.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
