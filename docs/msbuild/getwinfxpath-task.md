---
title: GetWinFXPath — — zadanie | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab8e15cef722e935dde322072f6834ba00be8bc5
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633970"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath task

Zadanie <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> zwraca katalog bieżącego środowiska uruchomieniowego .NET.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
|-------------------| - |
| `WinFXPath` | Opcjonalny parametr wyjściowy **ciągu** .<br /><br /> Określa rzeczywistą ścieżkę do środowiska uruchomieniowego .NET. |
| `WinFXNativePath` | Wymagany parametr **ciągu** .<br /><br /> Określa ścieżkę do natywnego środowiska uruchomieniowego .NET. |
| `WinFXWowPath` | Wymagany parametr **ciągu** .<br /><br /> Określa ścieżkę do zestawów .NET w 32-bitowym **systemie Windows w module systemu Windows** w systemach 64-bitowych. |

## <a name="remarks"></a>Uwagi

 Jeśli zadanie <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> jest wykonywane na procesorze 64-bitowym, parametr **WinFXPath** jest ustawiany na ścieżkę, która jest przechowywana w parametrze **WinFXWowPath** ; w przeciwnym razie parametr **WinFXPath** jest ustawiany na ścieżkę, która jest przechowywana w parametrze **WinFXNativePath** .

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak używać zadania **GetWinFXPath —** do wykrywania ścieżki natywnej do środowiska uruchomieniowego .NET.

```xml
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

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
