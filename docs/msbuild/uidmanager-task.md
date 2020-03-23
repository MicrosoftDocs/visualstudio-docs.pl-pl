---
title: Zadanie UidManager | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 37692c541fb2a6e9b2ccf61083dd383e56a79766
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631526"
---
# <a name="uidmanager-task"></a>Zadanie UidManager

Zadanie <xref:Microsoft.Build.Tasks.Windows.UidManager> sprawdza, aktualizuje lub usuwa unikatowe identyfikatory (UID), aby zlokalizować wszystkie elementy XAML, które są zawarte w źródłowych plikach XAML.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
|-------------------------| - |
| `IntermediateDirectory` | Opcjonalny parametr **String.**<br /><br /> Określa katalog używany do utworzenia kopii zapasowej źródłowych plików XAML określonych przez parametr **MarkupFiles.** |
| `MarkupFiles` | Wymagany parametr **ITaskItem[].**<br /><br /> Określa źródłowe pliki XAML, które mają być dołączane do sprawdzania, aktualizowania lub usuwania UID. |
| `Task` | Wymagany parametr **String.**<br /><br /> Określa zadanie zarządzania identyfikatorem UID, które chcesz wykonać. Prawidłowe opcje **to Sprawdź,** **Aktualizuj**lub **Usuń**. |

## <a name="example"></a>Przykład

 W poniższym przykładzie <xref:Microsoft.Build.Tasks.Windows.UidManager> użyto zadania, aby sprawdzić, czy określone źródłowe pliki XAML zawierają elementy XAML, które mają odpowiednie identyfikatory UID.

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
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Jak: Lokalizuj aplikację](/dotnet/framework/wpf/advanced/how-to-localize-an-application)