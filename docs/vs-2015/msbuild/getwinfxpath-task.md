---
title: GetWinFXPath — — zadanie | Microsoft Docs
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
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da32f0bfce9edf652e19df6b68bc51ed92624d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699019"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>Zadanie zwraca katalog bieżącego [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] środowiska uruchomieniowego.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`WinFXPath`|Opcjonalny parametr wyjściowy **ciągu** .<br /><br /> Określa rzeczywistą ścieżkę do [!INCLUDE[TLA2#tla_winfx](../includes/tla2sharptla-winfx-md.md)] środowiska uruchomieniowego.|  
|`WinFXNativePath`|Wymagany parametr **ciągu** .<br /><br /> Określa ścieżkę do natywnego [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] środowiska uruchomieniowego.|  
|`WinFXWowPath`|Wymagany parametr **ciągu** .<br /><br /> Określa ścieżkę do [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] zestawów w 32-bitowym **systemie Windows w module systemu Windows** w systemach 64-bitowych.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> zadanie jest wykonywane na procesorze 64-bitowym, parametr **WinFXPath** jest ustawiany na ścieżkę, która jest przechowywana w parametrze **WinFXWowPath** . w przeciwnym razie parametr **WinFXPath** jest ustawiony na ścieżkę, która jest przechowywana w parametrze **WinFXNativePath** .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać zadania **GetWinFXPath —** do wykrywania ścieżki natywnej [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] środowiska uruchomieniowego.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
