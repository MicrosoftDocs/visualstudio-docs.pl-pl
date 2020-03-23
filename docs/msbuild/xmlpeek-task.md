---
title: XmlPeek Zadanie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a76bf033fa3eb85f0626478b965285f32e5fb6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094663"
---
# <a name="xmlpeek-task"></a>XmlPeek — zadanie

Zwraca wartości określone przez XPath Query z pliku XML.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `XmlPeek` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Namespaces`|Parametr `String` opcjonalny.<br /><br /> Określa przestrzenie nazw prefiksów kwerend xpath.|
|`Query`|Parametr `String` opcjonalny.<br /><br /> Określa kwerendę XPath.|
|`Result`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera wyniki, które są zwracane przez to zadanie.|
|`XmlContent`|Parametr `String` opcjonalny.<br /><br /> Określa dane wejściowe XML jako ciąg.|
|`XmlInputPath`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa dane wejściowe XML jako ścieżkę pliku.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).



## <a name="example"></a>Przykład

Oto przykładowy plik `settings.config` XML do odczytania:

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

W tym przykładzie, jeśli `value`chcesz przeczytać , użyj kodu następującego:

```xml
<Target Name="BeforeBuild">
    <XmlPeek XmlInputPath="settings.config" Query="appSettings/add[@key='ProjectFolder']/@value">
        <Output TaskParameter="Result" ItemName="value" />
    </XmlPeek>
    <Message Text="Using project folder @(value)." Importance="high" />
    <PropertyGroup>
        <ProjectFolder>@(value)</ProjectFolder>
    </PropertyGroup>
    <ItemGroup>
        <Compile Include="Projects\$(ProjectFolder)\Controls\Control1.ascx.cs">
            <SubType>ASPXCodeBehind</SubType>
        </Compile>
    </ItemGroup>
</Target>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
