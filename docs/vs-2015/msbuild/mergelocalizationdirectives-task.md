---
title: MergeLocalizationDirectives — — zadanie | Microsoft Docs
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
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d6c2aa6cea687119e69b565da5468e8fa723641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703417"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives>Zadanie Scala atrybuty lokalizacji i komentarze jednego lub więcej [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików formatu binarnego w pojedynczym pliku dla całego zestawu.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Wymagany parametr **ITaskItem []** .<br /><br /> Określa listę plików dyrektyw lokalizacyjnych dla poszczególnych plików w [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] formacie binarnym.|  
|`OutputFile`|Wymagany parametr wyjściowy **ciągu** .<br /><br /> Określa ścieżkę wyjściową skompilowanego zestawu dyrektyw.|  
  
## <a name="remarks"></a>Uwagi  
 Można dodawać atrybuty lokalizacji i komentarze do [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] zawartości. Dzięki [!INCLUDE[TLA#tla_wpf](../includes/tlasharptla-wpf-md.md)] obsłudze lokalizacji można rozłożyć atrybuty lokalizacji i komentarze oraz umieścić je w pliku. loc, który jest oddzielony od wygenerowanego zestawu. Można to zrobić przy użyciu atrybutu **LocalizationPropertyStorage** . Aby uzyskać więcej informacji na temat atrybutów lokalizacji i komentarzy oraz **LocalizationPropertyStorage**, zobacz [atrybuty lokalizacji i komentarze](https://msdn.microsoft.com/library/ead2d9ac-b709-4ec1-a924-39927a29d02f).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład Scala Komentarze lokalizacyjne kilku [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików formatu binarnego w jeden plik. Loc.  
  
```  
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
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
