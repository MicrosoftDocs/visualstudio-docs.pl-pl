---
title: Zadanie klasyfikatora plików | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46ed1b1f94cd2ef23ff0704912cb2a2194ba7dab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634191"
---
# <a name="fileclassifier-task"></a>Zadanie Klasyfikatora plików

Zadanie <xref:Microsoft.Build.Tasks.Windows.FileClassifier> klasyfikuje zestaw zasobów źródłowych jako te, które zostaną osadzone w zestawie. Jeśli zasób nie jest zlokalizowany, jest osadzony w głównym zestawie aplikacji; w przeciwnym razie jest osadzony w zestawie satelicie.

## <a name="task-parameters"></a>Parametry zadania

|Parametr|Opis|
|---------------|-----------------|
|`CLREmbeddedResource`|Nieużywany.|
|`CLRResourceFiles`|Nieużywany.|
|`CLRSatelliteEmbeddedResource`|Nieużywany.|
|`Culture`|Opcjonalny parametr **String.**<br /><br /> Określa kulturę kompilacji. Ta wartość może być **null,** jeśli kompilacja jest nielokalizowalna. Jeśli **null**, wartość domyślna jest mała wartość, że **CultureInfo.InvariantCulture** zwraca.|
|`MainEmbeddedFiles`|Opcjonalny parametr **wyjściowy ITaskItem[].**<br /><br /> Określa zasoby nielokalizalne, które są osadzone w zestawie głównym.|
|`OutputType`|Wymagany parametr **String.**<br /><br /> Określa typ pliku, do który mają być osadzone określone pliki źródłowe. Prawidłowe wartości to **exe,** **winexe**lub **library**.|
|`SatelliteEmbeddedFiles`|Opcjonalny parametr **wyjściowy ITaskItem[].**<br /><br /> Określa pliki zlokalizowane, które są osadzone w zestawie satelicie dla kultury określonej przez **Culture** parametru.|
|`SourceFiles`|Wymagany parametr **ITaskItem[].**<br /><br /> Określa listę plików do sklasyfikowania.|

## <a name="remarks"></a>Uwagi

Jeśli **culture** parametr nie jest ustawiony, wszystkie zasoby, które są określone przy użyciu **SourceFiles** parametr są nielokalizowalne; w przeciwnym razie są one zlokalizowane, chyba że są one skojarzone z atrybutem **Localizable,** który jest ustawiony na **false**.

## <a name="example"></a>Przykład

Poniższy przykład klasyfikuje pojedynczy plik źródłowy jako zasób, a następnie osadza go w zestawie satelicie dla kultury francusko-kanadyjskiej (fr-CA).

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
