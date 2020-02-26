---
title: UidManager — zadanie | Microsoft Docs
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
ms.openlocfilehash: 312e174b1bbe0a21d155e4e6b5050e6f41dd8352
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579548"
---
# <a name="uidmanager-task"></a>UidManager, zadanie
Zadanie <xref:Microsoft.Build.Tasks.Windows.UidManager> sprawdza, aktualizuje lub usuwa unikatowe identyfikatory (UID), aby zlokalizować wszystkie elementy [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] zawarte w źródłowym pliku [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
|-------------------------| - |
| `IntermediateDirectory` | Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog, który jest używany do tworzenia kopii zapasowych plików [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] źródłowych, które są określone przez parametr **MarkupFiles** . |
| `MarkupFiles` | Wymagany parametr **ITaskItem []** .<br /><br /> Określa pliki źródłowe [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] do dołączenia do sprawdzania UID, aktualizowania lub usuwania. |
| `Task` | Wymagany parametr **ciągu** .<br /><br /> Określa zadanie zarządzania UID, które ma zostać wykonane. Prawidłowe opcje to **check**, **Update**lub **Remove**. |

## <a name="example"></a>Przykład
 Poniższy przykład używa zadania <xref:Microsoft.Build.Tasks.Windows.UidManager>, aby sprawdzić, czy określone źródłowe [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki zawierają [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] elementy, które mają odpowiednie identyfikatory UID.

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
- [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Instrukcje: lokalizowanie aplikacji](/dotnet/framework/wpf/advanced/how-to-localize-an-application)