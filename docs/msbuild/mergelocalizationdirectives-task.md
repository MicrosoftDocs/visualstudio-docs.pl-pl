---
title: MergeLocalizationDirectives — — zadanie | Microsoft Docs
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
ms.openlocfilehash: 86c689122ac0ddfd9441122fdead64ecd8049e72
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579628"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives —, zadanie
Zadanie <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> Scala atrybuty lokalizacji i komentarze jednego lub większej liczby plików w formacie binarnym [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] w pojedynczym pliku dla całego zestawu.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Wymagany parametr **ITaskItem []** .<br /><br /> Określa listę plików dyrektyw lokalizacyjnych dla poszczególnych plików w [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] formacie binarnym. |
| `OutputFile` | Wymagany parametr wyjściowy **ciągu** .<br /><br /> Określa ścieżkę wyjściową skompilowanego zestawu dyrektyw. |

## <a name="remarks"></a>Uwagi
Do zawartości [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] można dodawać atrybuty lokalizacji i komentarze. Dzięki obsłudze [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] lokalizacji można rozłożyć atrybuty lokalizacji i komentarze oraz umieścić je w pliku *. loc* , który jest oddzielony od wygenerowanego zestawu. Można to zrobić przy użyciu atrybutu **LocalizationPropertyStorage** . Aby uzyskać więcej informacji na temat atrybutów lokalizacji i komentarzy oraz **LocalizationPropertyStorage**, zobacz [atrybuty lokalizacji i komentarze](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Przykład
Poniższy przykład Scala Komentarze lokalizacyjne kilku [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików w formacie binarnym w jeden plik *. loc* .

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

## <a name="see-also"></a>Zobacz też
- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania programu MSBuild](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
