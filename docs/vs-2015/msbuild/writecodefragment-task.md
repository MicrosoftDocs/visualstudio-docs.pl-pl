---
title: WriteCodeFragment — Zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa9882d30a8483937f77da21bb4700d4899a68a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555481"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
