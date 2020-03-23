---
title: Zadanie ResourcesGenerator | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b5aba45292aaa55a719eb19d6f0f6f115e8b477
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632514"
---
# <a name="resourcesgenerator-task"></a>Zadanie ResourcesGenerator

Zadanie <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> osadza jeden lub więcej zasobów (*.jpg*, *.ico*, *.bmp*, XAML w formacie binarnym i inne typy rozszerzeń) do pliku *.resources.*

## <a name="task-parameters"></a>Parametry zadania

|Parametr|Opis|
|---------------|-----------------|
|`OutputPath`|Wymagany parametr **String.**<br /><br /> Określa ścieżkę katalogu wyjściowego. Jeśli ścieżka nie jest ścieżką bezwzględną, jest traktowana jako ścieżka względem katalogu projektu głównego.|
|`OutputResourcesFile`|Wymagany **parametr wyjściowy ITaskItem[].**<br /><br /> Określa ścieżkę i nazwę wygenerowanego pliku *.resources.* Jeśli ścieżka nie jest ścieżką bezwzględną, plik *.resources* jest generowany względem katalogu projektu głównego.|
|`ResourcesFiles`|Wymagany parametr **ITaskItem[].**<br /><br /> Określa jeden lub więcej zasobów do osadzenia w wygenerowanym pliku *.resources.*|

## <a name="example"></a>Przykład

 Poniższy przykład generuje plik *.resources* z jednym zasobem *.bmp.* Zasób *.bmp* jest generowany do katalogu, który jest względem katalogu głównego projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)