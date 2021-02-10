---
title: ResourcesGenerator — — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania ResourcesGenerator — do osadzenia jednego lub większej liczby zasobów w pliku Resources.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a26c8bfc29ca985a725deea6c75b14d68abb9eb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937891"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator, zadanie

<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator>Zadanie osadza jeden lub więcej zasobów (*. jpg*, *. ico*, *. bmp*, XAML w formacie binarnym i innych typów rozszerzenia) w pliku *resources* .

## <a name="task-parameters"></a>Parametry zadania

|Parametr|Opis|
|---------------|-----------------|
|`OutputPath`|Wymagany parametr **ciągu** .<br /><br /> Określa ścieżkę katalogu wyjściowego. Jeśli ścieżka nie jest ścieżką bezwzględną, jest traktowana jako ścieżka względem katalogu głównego projektu.|
|`OutputResourcesFile`|Wymagany parametr wyjściowy **ITaskItem []** .<br /><br /> Określa ścieżkę i nazwę wygenerowanego pliku *resources* . Jeśli ścieżka nie jest ścieżką bezwzględną, plik *resources* jest generowany względem katalogu głównego projektu.|
|`ResourcesFiles`|Wymagany parametr **ITaskItem []** .<br /><br /> Określa co najmniej jeden zasób do osadzenia w wygenerowanym pliku *resources* .|

## <a name="example"></a>Przykład

 Poniższy przykład generuje plik *resources* z pojedynczym zasobem *. bmp* . Zasób *. bmp* jest generowany do katalogu, który jest względny dla katalogu głównego projektu.

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
- [Dokumentacja zadań](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)