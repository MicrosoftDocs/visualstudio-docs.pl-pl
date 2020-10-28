---
title: MergeLocalizationDirectives — — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania MergeLocalizationDirectives — do scalania atrybutów lokalizacji i komentarzy plików binarnych XAML w jednym pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97d04978a2809a4744f62f27c375efdec1e43dcc
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903874"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives, zadanie

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives>Zadanie Scala atrybuty lokalizacji i komentarze jednego lub więcej plików formatu binarnego XAML do pojedynczego pliku dla całego zestawu.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Wymagany parametr **ITaskItem []** .<br /><br /> Określa listę plików dyrektyw lokalizacyjnych dla poszczególnych plików w formacie binarnym XAML. |
| `OutputFile` | Wymagany parametr wyjściowy **ciągu** .<br /><br /> Określa ścieżkę wyjściową skompilowanego zestawu dyrektyw. |

## <a name="remarks"></a>Uwagi

Możesz dodawać atrybuty lokalizacji i komentarze do zawartości XAML. Dzięki obsłudze lokalizacji Windows Presentation Foundation (WPF) można rozłożyć atrybuty lokalizacji i komentarze oraz umieścić je w pliku *. loc* , który jest oddzielony od wygenerowanego zestawu. Można to zrobić przy użyciu atrybutu **LocalizationPropertyStorage** . Aby uzyskać więcej informacji na temat atrybutów lokalizacji i komentarzy oraz **LocalizationPropertyStorage** , zobacz [atrybuty lokalizacji i komentarze](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Przykład

Poniższy przykład Scala Komentarze lokalizacyjne kilku plików w formacie binarnym XAML w jeden plik *. loc* .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MergeLocalizationDirectivesTask">
    <MergeLocalizationDirectives
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"
      OutputFile="obj\debug\WPFMSBuildSample.loc" />
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz także

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania programu MSBuild](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
