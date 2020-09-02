---
title: FileClassifier — — zadanie | Microsoft Docs
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
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2077b1df6d6362c924527e296d36c041e7bd9929
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693787"
---
# <a name="fileclassifier-task"></a>FileClassifier — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.FileClassifier>Zadanie klasyfikuje zestaw zasobów źródłowych jako te, które będą osadzone w zestawie. Jeśli zasób nie jest Lokalizowalny, jest osadzony w głównym zestawie aplikacji; w przeciwnym razie jest osadzony w zestawie satelickim.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Nieużywany.|  
|`CLRResourceFiles`|Nieużywany.|  
|`CLRSatelliteEmbeddedResource`|Nieużywany.|  
|`Culture`|Opcjonalny parametr **ciągu** .<br /><br /> Określa kulturę dla kompilacji. Ta wartość może być **równa null** , jeśli kompilacja nie jest lokalizowalna. Jeśli wartość jest **równa null**, wartością domyślną jest wartość małymi literami zwracaną przez **CultureInfo. InvariantCulture** .|  
|`MainEmbeddedFiles`|Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Określa nielokalizowalne zasoby, które są osadzone w zestawie głównym.|  
|`OutputType`|Wymagany parametr **ciągu** .<br /><br /> Określa typ pliku do osadzenia określonych plików źródłowych. Prawidłowe wartości to **exe**, **winexe**lub **Library**.|  
|`SatelliteEmbeddedFiles`|Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Określa pliki lokalizowalne osadzone w zestawie satelickim dla kultury określonej przez parametr **Culture** .|  
|`SourceFiles`|Wymagany parametr **ITaskItem []** .<br /><br /> Określa listę plików do klasyfikowania.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli parametr **Culture** nie jest ustawiony, wszystkie zasoby, które są określone za pomocą parametru **SourceFiles** , nie są lokalizowalne; w przeciwnym razie są one lokalizowalne, chyba że są skojarzone z **lokalizowalnym** atrybutem, który ma wartość **false**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład klasyfikuje pojedynczy plik źródłowy jako zasób, a następnie osadza go w zestawie satelitarnym dla kultury francuskiej — kanadyjskiej (fr-CA).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
