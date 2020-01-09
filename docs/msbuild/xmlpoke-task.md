---
title: XmlPoke — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f44ce4736900fde35716ca3ec9dabb2d55c6df51
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588385"
---
# <a name="xmlpoke-task"></a>XmlPoke — zadanie

Ustawia wartości określone przez zapytanie XPath w pliku XML.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `XmlPoke`.

|Parametr|Opis|
|---------------|-----------------|
|`Namespaces`|Opcjonalny parametr `String`.<br /><br /> Określa przestrzenie nazw dla prefiksów zapytania XPath. `Namespaces` to fragment kodu XML składający się z `Namespace` elementów z atrybutami `Prefix` i `Uri`. Atrybut `Prefix` Określa prefiks do skojarzenia z przestrzenią nazw określoną w atrybucie `Uri`. Nie należy używać pustej `Prefix`.|
|`Query`|Opcjonalny parametr `String`.<br /><br /> Określa zapytanie XPath.|
|`Value`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa wartość, która ma zostać wstawiona do określonej ścieżki.|
|`XmlInputPath`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa dane wejściowe w formacie XML jako ścieżkę pliku.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Oto przykład. XML do zmodyfikowania:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

W tym przykładzie, jeśli chcesz zmodyfikować `/Package/mp:PhoneIdentity/PhonePublisherId`, użyj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` jest używany jako prefiks sztucznej przestrzeni nazw dla domyślnej przestrzeni nazw.

## <a name="see-also"></a>Zobacz także

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
