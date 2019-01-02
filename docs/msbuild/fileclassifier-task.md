---
title: Fileclassifier — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e14ff5857676746c630bc8a7187571d3adb8f4e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820764"
---
# <a name="fileclassifier-task"></a>Fileclassifier — zadanie
<xref:Microsoft.Build.Tasks.Windows.FileClassifier> Zadań klasyfikuje zestaw zasobów źródłowego, jak te, które zostaną osadzone w zestawie. Jeśli zasób nie jest możliwych do zlokalizowania, jest osadzony w głównym zestawem aplikacji; w przeciwnym razie jest osadzony w zestawie satelickim.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Nieużywane.|  
|`CLRResourceFiles`|Nieużywane.|  
|`CLRSatelliteEmbeddedResource`|Nieużywane.|  
|`Culture`|Opcjonalnie **ciąg** parametru.<br /><br /> Określa kulturę dla kompilacji. Ta wartość może być **null** Jeśli kompilacja jest niemożliwe do zlokalizowania. Jeśli **null**, wartością domyślną jest wartość małej litery, która **CultureInfo.InvariantCulture** zwraca.|  
|`MainEmbeddedFiles`|Opcjonalnie **[] ITaskItem** parametr wyjściowy.<br /><br /> Określa zasoby niemożliwe do zlokalizowania, które są osadzone w głównym zestawie.|  
|`OutputType`|Wymagane **ciąg** parametru.<br /><br /> Określa typ pliku w celu osadzenia plików źródłowych określonej w. Prawidłowe wartości to **exe**, **winexe**, lub **biblioteki**.|  
|`SatelliteEmbeddedFiles`|Opcjonalnie **[] ITaskItem** parametr wyjściowy.<br /><br /> Określa możliwych do zlokalizowania plików, które są osadzone w zestawu satelickiego dla kultury określonej parametrem **kultury** parametru.|  
|`SourceFiles`|Wymagane **[] ITaskItem** parametru.<br /><br /> Określa listę plików do klasyfikowania.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli **kultury** parametr nie jest ustawiona, wszystkie zasoby, które są określone za pomocą **Pliki_źródłowe** parametru są niemożliwe do zlokalizowania; w przeciwnym razie są one możliwych do zlokalizowania, chyba że są one skojarzone z  **Lokalizowalne** atrybut, który jest ustawiony na **false**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład klasyfikuje jednym pliku źródłowym jako zasób i osadzenie go w zestawu satelickiego dla kultury French-Canadian (fr-CA).  
  
```xml  
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
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)