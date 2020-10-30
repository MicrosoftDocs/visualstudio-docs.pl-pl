---
title: UidManager — zadanie | Microsoft Docs
description: Dowiedz się, jak zadanie MSBuild UidManager sprawdza, aktualizuje lub usuwa unikatowe identyfikatory (UID), aby lokalizować wszystkie elementy XAML w źródłowych plikach XAML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 852b910de742676e1fe7dd0c85129640eb37a9ae
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046927"
---
# <a name="uidmanager-task"></a>UidManager, zadanie

<xref:Microsoft.Build.Tasks.Windows.UidManager>Zadanie sprawdza, aktualizuje lub usuwa unikatowe identyfikatory (UID) w celu zlokalizowania wszystkich elementów XAML, które są zawarte w źródłowym pliku XAML.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
|-------------------------| - |
| `IntermediateDirectory` | Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog, który jest używany do tworzenia kopii zapasowej źródłowych plików XAML, które są określone przez parametr **MarkupFiles** . |
| `MarkupFiles` | Wymagany parametr **ITaskItem []** .<br /><br /> Określa pliki źródłowe XAML, które mają być używane do sprawdzania UID, aktualizowania lub usuwania. |
| `Task` | Wymagany parametr **ciągu** .<br /><br /> Określa zadanie zarządzania UID, które ma zostać wykonane. Prawidłowe opcje to **check** , **Update** lub **Remove** . |

## <a name="example"></a>Przykład

 Poniższy przykład używa zadania, <xref:Microsoft.Build.Tasks.Windows.UidManager> Aby sprawdzić, czy określone źródłowe pliki XAML zawierają elementy XAML, które mają odpowiednie identyfikatory UID.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Dokumentacja zadań](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Instrukcje: lokalizowanie aplikacji](/dotnet/framework/wpf/advanced/how-to-localize-an-application)