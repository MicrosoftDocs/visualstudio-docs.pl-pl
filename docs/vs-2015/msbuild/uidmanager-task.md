---
title: UidManager — zadanie | Microsoft Docs
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
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5fd8175911def7fb1b63dc63d967c404d649e9e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703697"
---
# <a name="uidmanager-task"></a>UidManager — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.UidManager>Zadanie sprawdza, aktualizuje lub usuwa unikatowe identyfikatory (UID) w celu zlokalizowania wszystkich [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] elementów uwzględnionych w [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plikach źródłowych.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`IntermediateDirectory`|Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog, który jest używany do tworzenia kopii zapasowych [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików źródłowych, które są określone przez parametr **MarkupFiles** .|  
|`MarkupFiles`|Wymagany parametr **ITaskItem []** .<br /><br /> Określa pliki źródłowe [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] , które mają być objęte sprawdzaniem UID, aktualizowaniem lub usuwaniem.|  
|`Task`|Wymagany parametr **ciągu** .<br /><br /> Określa zadanie zarządzania UID, które ma zostać wykonane. Prawidłowe opcje to **check**, **Update**lub **Remove**.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa zadania, <xref:Microsoft.Build.Tasks.Windows.UidManager> Aby sprawdzić, czy określone pliki źródłowe [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] zawierają [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] elementy, które mają odpowiednie identyfikatory UID.  
  
```  
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
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Jak lokalizować aplikację](https://msdn.microsoft.com/library/5001227e-9326-48a4-9dcd-ba1b89ee6653)
